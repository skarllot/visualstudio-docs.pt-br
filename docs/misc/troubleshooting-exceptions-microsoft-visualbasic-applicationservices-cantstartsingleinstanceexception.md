---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção CantStartSingleInstanceException"
  - "Exceção Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
A exceção que é lançada quando a segunda instância de um aplicativo de instância única não pôde se conectar à instância original.  
  
## Comentários  
 Possíveis causas desse problema incluem:  
  
-   A instância original parou de responder.  
  
-   O aplicativo não tem permissões para criar objetos kernel.  
  
     O nome de base para os objetos kernel vem da concatenação GUID, número de versão principal e número da versão secundária do assembly. Por exemplo, o nome de base poderia ser 3639f15d\-9547\-43da\-8145\-60da 347829915.1.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)