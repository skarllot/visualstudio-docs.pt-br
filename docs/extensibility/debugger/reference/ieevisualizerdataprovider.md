---
title: IEEVisualizerDataProvider | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
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
ms.openlocfilehash: 7ddbdfee00f0a8a17216f437450ceb4a8caec816
ms.lasthandoff: 02/22/2017

---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface fornece a capacidade de alterar o valor de um objeto por meio de um visualizador de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão implementa essa interface para oferecer suporte a modificação dos dados em um objeto de propriedade por meio de um visualizador de tipo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é usada na criação de [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto por meio de uma chamada para [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Consulte [visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter mais detalhes.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina se é possível atualizar o objeto (e em seguida, seu valor) que este visualizador está representando.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Força uma reavaliação do objeto para esse visualizador.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtém um objeto existente para esse visualizador (nenhuma avaliação é feita).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Atualiza o objeto para esse visualizador, alterando assim o valor que apresenta o visualizador.|  
  
## <a name="remarks"></a>Comentários  
 O serviço visualizador (conforme representado pelo [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) de interface e retornado por [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantém uma referência para o objeto que implementa o `IEEVisualizerDataProvider` interface. Como resultado, o `IEEVisualizerDataProvider` interface não deve ser implementada no mesmo objeto que implementa o [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se esse objeto mantém uma referência para o `IEEVisualizerService` objeto: resulta de uma referência circular e um deadlock ocorre quando os objetos são destruídos. A abordagem recomendada é implementar `IEEVisualizerDataProvider` em um objeto separado para que o `IDebugProperty2` objeto delegados sem chamar `IUnknown::AddRef` nele.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)
