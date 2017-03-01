---
title: IDebugEnumField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
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
ms.openlocfilehash: 3c0e6e0b8fc99899c6cb4186a256571ce64053eb
ms.lasthandoff: 02/22/2017

---
# <a name="idebugenumfield"></a>IDebugEnumField
Essa interface representa um tipo de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface para representar uma enumeração.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/visual-cpp/atl/queryinterface) para obter essa interface da [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retorna `FIELD_TYPE_ENUM`.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem VTable  
 Além dos métodos de `IDebugField` e `IDebugContainerField` interfaces, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) descrevendo o nome para esse tipo de enumeração.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Retorna o nome da constante de enumeração associado o determinado valor.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Retorna o valor associado ao nome de constante de enumeração específico|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Retorna o valor associado com o nome de constante de enumeração específico, mas ignora maiusculas/minúsculas.|  
  
## <a name="remarks"></a>Comentários  
 É o símbolo subjacente que realmente está associado a um local com [ligar](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Ligação](../../../extensibility/debugger/reference/idebugbinder-bind.md)
