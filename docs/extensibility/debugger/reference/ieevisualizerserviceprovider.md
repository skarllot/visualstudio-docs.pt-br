---
title: IEEVisualizerServiceProvider | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 17
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
ms.openlocfilehash: 1a7e028da7cd14e164e86ef693ddc4e573ffa861
ms.lasthandoff: 02/22/2017

---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface fornece acesso a um método que pode criar um serviço de visualizador, que é usado para lidar com tarefas de Visualizador de tipo para o IDE.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O Visual Studio implementa essa interface para criar um objeto de serviço do visualizador, que por sua vez é usado para fornecer IDs de classe (`CLSID`s) de visualizadores de tipo para o Visual Studio IDE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O avaliador de expressão (EE) chama [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Cria o serviço Visualizador|  
  
## <a name="remarks"></a>Comentários  
 O `IEEVisualizerServiceProvider` interface é obtida durante a implementação de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). O serviço visualizador que cria essa interface é usado para fornecer funcionalidade para um [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface, que o EE é responsável pela implementação. O EE também é responsável por implementar uma [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface que permite que os visualizadores de tipo exibir e modificar o valor da propriedade.  
  
 Consulte [visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre como essas interfaces interagem.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)
