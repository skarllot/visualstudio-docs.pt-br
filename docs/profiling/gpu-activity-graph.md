---
title: "Gráfico de Atividade de GPU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f2ae1cc3783a9c1bd3f95b3be6df707bab4de64f

---
# <a name="gpu-activity-graph"></a>Gráfico de atividade de GPU
O gráfico de Atividade de GPU na Visualização Simultânea exibe o nível de atividade do DirectX no sistema, medido pelo número de mecanismos do DirectX em uso ao longo do tempo.  O gráfico não mostra quais mecanismos específicos foram usados.  É considerado que um mecanismo está em uso se ele estiver processando qualquer trabalho da GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Cores do gráfico de Atividade de GPU  
 Verde indica o consumo de mecanismos do DirectX pelo processo atual.  
  
 Cinza claro indica o consumo de mecanismos do DirectX por outros processos no sistema. Para reduzir o consumo de mecanismos do DirectX por outros processos, reduza o número de outros processos em execução no sistema.  
  
 Branco indica a disponibilidade de mecanismos do DirectX não utilizados no sistema. Esses mecanismos estão disponíveis para seu processo se você puder encontrar mais oportunidades de explorá-los. Alguns mecanismos só podem ser usados para tipos específicos de tarefas.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição da utilização](../profiling/utilization-view.md)


<!--HONumber=Feb17_HO4-->


