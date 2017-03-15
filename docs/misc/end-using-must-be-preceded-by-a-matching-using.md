---
title: "&#39;End Using&#39; deve ser precedido por um &#39;Using&#39; correspondente | Microsoft Docs"
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
  - "bc36007"
  - "vbc36007"
helpviewer_keywords: 
  - "BC36007"
ms.assetid: 10fb31ba-9b6c-403f-bacc-c7b5df14f1dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Using&#39; deve ser precedido por um &#39;Using&#39; correspondente
Um `End Using` instrução aparece sem associação `Using` declaração anterior.  
  
 **ID do erro:** BC36007  
  
### Para corrigir este erro  
  
-   Remover o `End Using` instrução se ela é redundante.  
  
-   Forneça a [Instrução Using](/dotnet/visual-basic/language-reference/statements/using-statement) se uma estiver ausente.  
  
-   Mova o `End Using` instrução até o local apropriado no código.  
  
## Consulte também  
 [Instrução End \<keyword\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)