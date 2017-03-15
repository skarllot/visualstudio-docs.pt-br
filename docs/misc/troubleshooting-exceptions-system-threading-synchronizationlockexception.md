---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Threading.SynchronizationLockException | Microsoft Docs"
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
  - "Exceção SynchronizationLockException"
  - "Exceção System.Threading.SynchronizationLockException"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Threading.SynchronizationLockException
A exceção que é lançada quando um método requer que o chamador possua o bloqueio em um determinado `Monitor`, e o método é invocado por um chamador que não possui o bloqueio.  
  
## Comentários  
 A <xref:System.Threading.SynchronizationLockException> é gerada chamando o <xref:System.Threading.Monitor.Exit%2A>, <xref:System.Threading.Monitor.Pulse%2A>, <xref:System.Threading.Monitor.PulseAll%2A>, e <xref:System.Threading.Monitor.Wait%2A> métodos o `Monitor` classe a partir de um bloco de código não sincronizado.  
  
## Consulte também  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)