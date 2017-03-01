---
title: IDebugArrayField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
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
ms.openlocfilehash: e73ab513461077ed44bec2eed7410f5317fb6a4e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayfield"></a>IDebugArrayField
Essa interface descreve um tipo ou um símbolo de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface. Essa interface é uma especialização que representa objetos de matriz.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/visual-cpp/atl/queryinterface) para obter essa interface da [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retorna o sinalizador `FIELD_TYPE_ARRAY`.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, essa interface implementa o seguinte:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Obtém o número de elementos na matriz.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Obtém o tipo de elemento na matriz.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Obtém a classificação da matriz.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
