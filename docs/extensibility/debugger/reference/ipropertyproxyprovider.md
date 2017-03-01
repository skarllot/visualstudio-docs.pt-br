---
title: IPropertyProxyProvider | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
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
ms.openlocfilehash: 5bc64c1a2c81e1a4f523edcd958e924e5e8f3303
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Essa interface fornece uma interface de proxy para exibir e alterar dados de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão (EE) implementa essa interface no mesmo objeto que implementa o [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface como parte do suporte do EE de visualizadores de tipo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em um `IDebugProperty3` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 O `IPropertyProxyProvider` interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera uma interface de proxy de propriedade para exibir dados em um objeto.|  
  
## <a name="remarks"></a>Comentários  
 Embora o EE implementa essa interface, a implementação de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) normalmente é controlada por [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Consulte [visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre como obter a interface IEEVisualizerService.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)
