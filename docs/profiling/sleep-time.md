---
title: "Tempo de suspens&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "Visualizador de Simultaneidade, Tempo de suspensão"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tempo de suspens&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esses segmentos na linha do tempo estão associados com a hora de bloqueio que são categorizados como o estado suspenso.  A categoria de suspensão indica que um thread deu voluntariamente acima o núcleo lógico e não está fazendo nenhum trabalho.  Durante esse tempo, um thread foi bloqueado na API do visualizador de simultaneidade é contado como o estado suspenso.  APIs como `Sleep()` e `SwitchToThread()` se enquadram neste grupo.  
  
## Consulte também  
 [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)