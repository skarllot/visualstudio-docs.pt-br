---
title: "Exibição de núcleos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
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
ms.openlocfilehash: 128cc66b513b3d6afd8dd5c88f603af8c581450b

---
# <a name="cores-view"></a>Exibição de núcleos
A Exibição de Núcleos mostra como a execução do thread foi mapeada para os núcleos de processador lógico. Se você estiver escrevendo aplicativos de servidor, essa exibição poderá ajudá-lo a otimizar o desempenho de cache usando o gerenciamento do pool de threads ou a afinidade de thread. Ela também pode ajudá-lo a examinar os casos em que o uso da afinidade de thread pode ter piorado o problema da migração de núcleo cruzado. A Exibição de Núcleos tem duas partes: um gráfico e uma legenda.  
  
 O gráfico mostra os núcleos lógicos no eixo Y e o tempo no eixo X. Cada thread no gráfico tem uma cor exclusiva para que seja possível acompanhar seu movimento entre os núcleos ao longo do tempo. É possível filtrar os threads nesse gráfico selecionando-os na área de legenda.  
  
 A área de legenda tem uma entrada para cada cor no gráfico. Cada entrada mostra a cor e o nome do thread, o número de alternâncias de contexto de núcleo cruzado, o número total de alternâncias de contexto e o percentual de alternâncias de contexto que cruzam núcleos. A legenda é classificada pelo número de alternâncias de contexto de núcleo cruzado, em ordem decrescente. Ela lista apenas os threads executados durante o intervalo de tempo exibido.  A lista será atualizada se você aplicar zoom ou movimento panorâmico.  
  
## <a name="see-also"></a>Consulte também  
 [Visualização Simultânea](../profiling/concurrency-visualizer.md)   
 [Exibição Utilização](../profiling/utilization-view.md)   
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)


<!--HONumber=Feb17_HO4-->


