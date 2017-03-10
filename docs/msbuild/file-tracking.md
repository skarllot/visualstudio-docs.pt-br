---
title: "Acompanhamento de arquivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, controle de arquivos"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Acompanhamento de arquivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Chamadas de logs de rastreamento de arquivo para o sistema de arquivos do Windows para um processo e seus processos filhos.  Ao chamar as funções listadas a seguir, os programas controlam quando ativar e desativar o registro e especificam o arquivo de log para uso.  
  
## Nesta seção  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Parar de acompanhar o contexto atual.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Retome o acompanhamento após uma chamada para [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Defina o número de threads a ser usado para acompanhamento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Inicie um novo contexto de acompanhamento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Inicie um novo contexto de acompanhamento com uma raiz especificada.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Encerrar o rastreamento e liberar os recursos utilizados.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Suspender o acompanhamento temporariamente.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Escreva os logs de rastreamento para todos os contextos.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Escreva o log de rastreamento para o contexto atual.