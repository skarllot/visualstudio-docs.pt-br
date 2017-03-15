---
title: "Fiber n&#227;o agendado | Microsoft Docs"
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
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fiber n&#227;o agendado
O depurador não pode avaliar uma expressão porque ele está em uma fibra lógica que não está agendada em um segmento físico. Isso pode acontecer se o processo é executado em um servidor SQL usando fibras.  
  
 Uma fibra consiste de uma pilha e um contexto de registro, e ele pode ser executado em qualquer thread. Uma fibra pode ser trocada fora de um segmento e reiniciada posteriormente em um thread diferente.  
  
 **ID do erro:** BC30948  
  
### Para corrigir este erro  
  
-   Certifique\-se de que fibra está agendada em um segmento físico.  
  
## Consulte também  
 [Debugging SQL](http://msdn.microsoft.com/pt-br/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)