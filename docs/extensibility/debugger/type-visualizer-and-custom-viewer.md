---
title: Digite visualizador e visualizador personalizado | Documentos do Microsoft
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
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
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
ms.openlocfilehash: 1f3a5f82e3256f1dc1a979d4de36ee3f7124da81
ms.lasthandoff: 02/22/2017

---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipo e o visualizador personalizado
Um visualizador de tipo é um componente que exibe uma parte dos dados em um formato muito específico. Esse formato é inteiramente o implementador do visualizador, o usuário final ou um fornecedor de terceiros de visualizadores.  
  
 Um visualizador personalizado é a parte de um avaliador de expressão personalizado que exibe uma parte dos dados em um formato muito específico. Esse formato é inteiramente o implementador do visualizador personalizado, o que significa que o formato cabe ao implementador do avaliador de expressão (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Suporte para visualizadores de tipo em um avaliador de expressão  
 Um EE pode oferecer suporte a visualizadores de tipo, oferecendo suporte a um conjunto de interfaces acessíveis aos visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). No entanto, observe que o EE não é responsável por implementar o Visualizador de tipo em si: o EE simplesmente permite visualizadores externos acessem as informações de tipo. Esses visualizadores podem ser enviados junto com o EE e instalados no local adequado no Visual Studio, fornecido por outro fornecedor de terceiros ou até mesmo pelo usuário final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Suporte para visualizadores personalizados em um avaliador de expressão  
 Um EE também pode oferecer suporte a visualizadores personalizados na qual o EE próprio fornece o código para exibir o tipo de dados. Um visualizador personalizado implementa o [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface, que lida com todas as tarefas de mostrar os dados em qualquer formato desejado; o visualizador tem controle total sobre a exibição e pode até permitir que os dados sejam modificados. Qualquer visualizadores personalizados fornecidos pelo EE acompanham o EE quando o produto é lançado.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)   
 [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
