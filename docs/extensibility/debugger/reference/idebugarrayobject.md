---
title: IDebugArrayObject | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
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
ms.openlocfilehash: b9ffd6eebb533cea6d5d24b2f95b58bb0b7e868b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface representa um objeto de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão implementa essa interface para representar uma matriz.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pode obter essa interface usando [QueryInterface](/visual-cpp/atl/queryinterface) se o objeto representa uma matriz.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de `IDebugObject` interface, os seguintes métodos são implementados no `IDebugArrayObject` interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtém a contagem de elementos na matriz.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtém um elemento da matriz.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtém todos os elementos da matriz.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtém a classificação da matriz.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtém as dimensões da matriz.|  
  
## <a name="remarks"></a>Comentários  
 Um avaliador de expressão usa essa interface para representar matrizes em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
