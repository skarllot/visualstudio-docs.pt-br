---
title: "Tempo de gerenciamento da memória | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
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
ms.openlocfilehash: d563c4790260cf91c3a0cbbd3410aa944b46da81

---
# <a name="memory-management-time"></a>Hora de gerenciamento da memória
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Gerenciamento da Memória. Isso significa que um thread é bloqueado por um evento associado uma operação de gerenciamento de memória, como paginação. Durante esse tempo, um thread foi bloqueado em um estado de API ou kernel que a Visualização Simultânea está contando como gerenciamento de memória. Eles incluem eventos como paginação e alocação de memória.  
  
 Examine os relatórios de perfil e as pilhas de chamada associados para entender melhor os motivos subjacentes para os bloqueios categorizados como Gerenciamento de Memória.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)


<!--HONumber=Feb17_HO4-->


