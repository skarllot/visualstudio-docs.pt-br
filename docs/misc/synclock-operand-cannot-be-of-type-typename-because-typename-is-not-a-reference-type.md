---
title: "Operando &#39;SyncLock&#39; n&#227;o pode ser do tipo &#39;&lt; typename &gt;&#39; porque &#39;&lt; typename &gt;&#39; n&#227;o &#233; um tipo de refer&#234;ncia | Microsoft Docs"
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
  - "vbc30582"
  - "bc30582"
helpviewer_keywords: 
  - "BC30582"
ms.assetid: 953aecf2-629a-4272-94bd-abf88f785e63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operando &#39;SyncLock&#39; n&#227;o pode ser do tipo &#39;&lt; typename &gt;&#39; porque &#39;&lt; typename &gt;&#39; n&#227;o &#233; um tipo de refer&#234;ncia
O `SyncLock` permite que instruções sejam sincronizadas em uma única expressão, garantindo que vários segmentos não executem as mesmas instruções ao mesmo tempo. O tipo de expressão em uma `SyncLock` instrução deve ser um tipo de referência, como uma classe, um módulo, uma interface, uma matriz ou um representante.  
  
 **ID do erro:** BC30582  
  
### Para corrigir este erro  
  
-   Altere o tipo para um tipo de referência apropriado.  
  
## Consulte também  
 [Instrução SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)   
 [NÃO está em compilação: Multithreading em Visual Basic](http://msdn.microsoft.com/pt-br/c731a50c-09c1-4468-9646-54c86b75d269)