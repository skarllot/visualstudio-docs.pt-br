---
title: "Tempo de Suspensão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7bb92b43d75891c123fbd120b5bb7fadddc44f37
ms.lasthandoff: 02/22/2017

---
# <a name="sleep-time"></a>Tempo de suspensão
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Suspensão. A categoria de suspensão indica que um thread voluntariamente cedeu seu núcleo lógico e não está trabalhando. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como suspensão. APIs como `Sleep()` e `SwitchToThread()` pertencem a esse grupo.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)
