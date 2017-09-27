---
title: "Exemplo de implementação de avaliação de expressão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ca872421d20d1d1a85cb2c5db621de28adee356d
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="sample-implementation-of-expression-evaluation"></a>Exemplo de implementação de avaliação de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Para uma **inspecionar** expressão de janela, o Visual Studio chamadas [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para produzir um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. `IDebugExpressionContext2::ParseText`instancia um avaliador de expressão (EE) e chama [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obter um [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.  
  
 Essa implementação de `IDebugExpressionEvaluator::Parse` executa as seguintes tarefas:  
  
1.  [C++] Analisa a expressão para procurar por erros.  
  
2.  Instancia uma classe (chamado `CParsedExpression` neste exemplo) que implementa o `IDebugParsedExpression` interface e a armazena na classe a expressão a ser analisado.  
  
3.  Retorna o `IDebugParsedExpression` de interface do `CParsedExpression` objeto.  
  
> [!NOTE]
>  Nos exemplos a seguir e no exemplo MyCEE, o avaliador de expressão não separa a análise da avaliação.  
  
## <a name="managed-code"></a>Código gerenciado  
 Esta é uma implementação de `IDebugExpressionEvaluator::Parse` em código gerenciado. Observe que esta versão do método adia a análise para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) como o código para análise também avalia ao mesmo tempo (consulte [avaliar uma expressão de inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Código não gerenciado  
 Esta é uma implementação de `IDebugExpressionEvaluator::Parse` em código não gerenciado. Este método chama uma função auxiliar, `Parse`, para analisar a expressão e verifique se há erros, mas esse método ignora o valor resultante. A avaliação formal é adiada para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) onde a expressão é analisada enquanto ele é avaliado (consulte [avaliar uma expressão de inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Avaliar uma expressão de janela Inspeção](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Avaliar uma expressão de Inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)
