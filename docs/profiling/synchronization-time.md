---
title: "Tempo de sincroniza&#231;&#227;o | Microsoft Docs"
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
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "Visualizador de Simultaneidade, Tempo de sincronização"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tempo de sincroniza&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esses segmentos na linha do tempo estão associados com a hora de bloqueio que são categorizados como a sincronização.  Quando um thread é marcado como bloqueado na sincronização, uma destas coisas será implícito:  
  
-   A execução do thread pode ter resultado a uma chamada para uma sincronização conhecido API de thread como `EnterCriticalSection()` ou `WaitForSingleObject()`.  
  
-   O algoritmo compatível de API não pode ser totalmente abrangente e, consequentemente algumas APIs que podem ser mapeados para outras categorias também podem aparecer como a sincronização como um quadro na pilha de chamadas atingiu se houver um kernel subjacente que bloqueia o primitivo que foi mapeado para essa categoria.  
  
 Para entender a causa subjacente para um evento de bloqueio de thread, revise cuidadosamente as chamadas de pilhas bloqueando e analisar relatórios.  
  
## Consulte também  
 [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)