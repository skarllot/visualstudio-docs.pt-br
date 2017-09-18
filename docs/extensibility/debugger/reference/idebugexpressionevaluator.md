---
title: IDebugExpressionEvaluator | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9fe4691fbd5c043739caeb06424de99586b12097
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface representa o avaliador de expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador da expressão deve implementar essa interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Para obter essa interface, instanciar o avaliador de expressão por meio de `CoCreateInstance` método usando a classe CLSID (identificador) do avaliador. Consulte o exemplo.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugExpressionEvaluator`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Converte uma cadeia de caracteres de expressão em uma expressão analisada.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtém as variáveis locais, argumentos e outras propriedades de um método.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Converte o método local e o deslocamento em um endereço de memória.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Determina qual idioma usar para criar resultados de impressão.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Define a raiz do registro. Usado para depuração lado a lado.|  
  
## <a name="remarks"></a>Comentários  
 Em uma situação típica, o mecanismo de depuração (DE) instancia o avaliador de expressão (EE) como resultado de uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Como o DE sabe o idioma e o fornecedor de EE que deseja usar, o DE obtém CLSID do EE do registro (o [SDK auxiliares para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) função, `GetEEMetric`, ajuda com a recuperação).  
  
 Após o EE é instanciado, o DE chama [analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) analisar a expressão e armazená-lo em uma [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objeto. Posteriormente, uma chamada para [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) avalia a expressão.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como instanciar o avaliador de expressão dado um provedor de símbolo e um endereço no código-fonte. Este exemplo usa uma função, `GetEEMetric`, do [SDK auxiliares para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib.  
  
```cpp#  
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,  
                                                 IDebugAddress *pSourceAddress)  
{  
    // This is typically defined globally but is specified here just  
    // for this example.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
  
    IDebugExpressionEvaluator *pEE = NULL;  
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {  
        HRESULT hr         = S_OK;  
        GUID  languageGuid = { 0 };  
        GUID  vendorGuid   = { 0 };  
  
        hr = pSymbolProvider->GetLanguage(pSourceAddress,  
                                          &languageGuid,  
                                          &vendorGuid);  
        if (SUCCEEDED(hr)) {  
            CLSID clsidEE      = { 0 };  
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;  
            // Get the expression evaluator's CLSID from the registry.  
            ::GetEEMetric(languageGuid,  
                          vendorGuid,  
                          metricCLSID,  
                          &clsidEE,  
                          strRegistrationRoot);  
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {  
                // Instantiate the expression evaluator.  
                spExpressionEvaluator.CoCreateInstance(clsidEE);  
            }  
            if (spExpressionEvaluator != NULL) {  
                pEE = spExpressionEvaluator.Detach();  
            }  
        }  
    }  
    return pEE;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
