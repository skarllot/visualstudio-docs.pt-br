---
title: "N&#227;o &#233; poss&#237;vel obter um fluxo para o log | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel obter um fluxo para o log
Não é possível obter um fluxo para o log. Possíveis nomes de arquivo com base em \< nome \> já estão em uso.  
  
 O <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe não pôde criar um novo arquivo de log porque todos os nomes de arquivo de log potenciais com base em \< nome \> já estão em uso.  
  
 Ter muitos arquivos de log pode indicar um problema de arquitetura com o aplicativo. Consulte a documentação para o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe para obter mais informações.  
  
### Para corrigir este erro  
  
1.  Definir o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> propriedade <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> para incluir um carimbo de data no nome do arquivo de log.  
  
2.  Arquive os logs existentes e remova\-os do computador para permitir que o <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objeto para criar novos logs.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [Objeto My.Application.Log](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [Objeto My.Log](/dotnet/visual-basic/language-reference/objects/my-log-object)