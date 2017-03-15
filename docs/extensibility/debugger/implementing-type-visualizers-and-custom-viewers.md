---
title: Implementando os visualizadores de tipo e visualizadores personalizados | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
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
ms.openlocfilehash: 7ce3b9c5a38d5a84701b44ca0103a81beba74ca2
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementando os visualizadores de tipo e visualizadores personalizados
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visualizadores de tipo e visualizadores personalizados permitem que um usuário exibir dados de um tipo específico de forma que seja mais significativa do que um simple despejo hexadecimal de números. Um avaliador de expressão (EE) pode associar visualizadores personalizados com tipos específicos de dados ou variáveis. Esses visualizadores personalizados são implementados com o EE. O EE também pode oferecer suporte a visualizadores de tipo externo, que podem vir de outro fornecedor de terceiros ou até mesmo o usuário final.  
  
## <a name="discussion"></a>Discussão  
  
### <a name="type-visualizers"></a>Visualizadores de tipo  
 O Visual Studio solicita uma lista de visualizadores de tipo e visualizadores personalizados para cada objeto a ser exibido em uma janela de inspeção. Um avaliador de expressão (EE) fornece essa lista para todos os tipos para os quais deseja oferecer suporte a visualizadores de tipo e visualizadores personalizados. Chamadas para [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) iniciar todo o processo de acessar os visualizadores de tipo e visualizadores personalizados (consulte [visualizando e exibindo dados](../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre a sequência de chamada).  
  
### <a name="custom-viewers"></a>Visualizadores personalizados  
 Visualizadores personalizados são implementados no EE para um tipo específico de dados e são representados pelo [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface. Um visualizador personalizado não é tão flexível quanto um visualizador de tipo, pois ele está disponível somente quando o EE que implementa esse visualizador personalizado específico está em execução. Implementar um visualizador personalizado é mais simples do que a implementação de suporte para visualizadores de tipo. No entanto, visualizadores de tipo de suporte fornece máxima flexibilidade para o usuário final para a visualização de dados de seu. O restante desta discussão aborda apenas os visualizadores de tipo.  
  
## <a name="interfaces"></a>Interfaces  
 O EE implementa as interfaces a seguir para dar suporte a visualizadores de tipo, a ser consumida pelo Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 O EE consome as seguintes interfaces para dar suporte a visualizadores de tipo:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizando e exibindo dados](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
