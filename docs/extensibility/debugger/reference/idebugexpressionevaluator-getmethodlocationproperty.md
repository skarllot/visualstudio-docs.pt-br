---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
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
ms.openlocfilehash: bdb0598a62de6b16ae8843d61b9346cb86d5cc9e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Este método converte o método local e o deslocamento em um endereço de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] O método local e o deslocamento, expresso como uma cadeia de caracteres.  
  
 `pSymbolProvider`  
 [in] O provedor de símbolo expresso como uma [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.  
  
 `pAddress`  
 [in] Um endereço dentro do método, expressado como uma [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto.  
  
 `pBinder`  
 [in] O fichário expresso como uma [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.  
  
 `ppProperty`  
 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o endereço de memória.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O endereço retornado pode ser usado para definir um ponto de interrupção, por exemplo.  
  
 Apesar do nome `upstrFullyQualifiedMethodPlusOffset`, esse parâmetro pode ser passado como um nome de método parcialmente qualificadas. Nesse caso, o método selecionado é aquele que inclui `pAddress`. Como esse parâmetro é interpretado é até a implementação do avaliador de expressão e o idioma que ele oferece suporte.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
