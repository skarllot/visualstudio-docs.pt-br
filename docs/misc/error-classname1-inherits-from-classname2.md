---
title: "&lt; erro &gt;: &#39;&lt; classname1 &gt;&#39; herda de &#39;&lt; classname2 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; erro &gt;: &#39;&lt; classname1 &gt;&#39; herda de &#39;&lt; classname2 &gt;&#39;
Foi detectada uma hierarquia de herança circular. Uma classe é designada como herança de si mesmo ou de outra classe que herda diretamente ou no final dela.  
  
 Essa mensagem pode aparecer mais de uma vez, para rastrear o caminho de herança circular.  
  
 **ID do erro:** BC30256  
  
### Para corrigir este erro  
  
-   Quebre a circularidade removendo pelo menos um `Inherits` instrução no caminho de herança circular.  
  
## Consulte também  
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)