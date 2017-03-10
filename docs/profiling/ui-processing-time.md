---
title: "Tempo de processamento de interface do usu&#225;rio | Microsoft Docs"
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
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "Visualizador de Simultaneidade, Tempo de processamento de interface do usuário"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tempo de processamento de interface do usu&#225;rio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esses segmentos na linha de tempo são associados com os tempos de bloqueio que são categorizados como processamento da interface do usuário.  Isso significa que um segmento está transmitindo mensagens do Windows ou está executando outro trabalho de interface do usuário \(UI\).  Durante este momento, um segmento foi bloqueado na API que o visualizador de simultaneidade está contando como processamento de interface do usuário.  APIs como `GetMessage()` e `MsgWaitForMultipleObjects()` se enquadram neste grupo.  
  
 Se nenhuma API bloqueadora predefinida é identificada, revise as pilhas de chamadas e análise de relatórios para determinar as causas subjacentes do atraso.  
  
 A categoria de processamento da interface do usuário é importante para entender a resposta de aplicativos de GUI, e é desejável em aplicativos que dependam da resposta da interface do usuário.  Por exemplo, se o encadeamento de interface do usuário em um aplicativo obtém tempo de 100% no processamento da interface do usuário, provavelmente ele é muito responsivo.  No entanto, se o encadeamento de interface do usuário gasta um tempo considerável em outras categorias, procure as causas e considere opções para reduzir categorias não relativas a interface do usuário naquele segmento.  
  
## Consulte também  
 [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)