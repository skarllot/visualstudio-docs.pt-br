---
title: "&#39;End Class&#39; deve ser precedido por uma &#39;Class&#39; correspondente | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Class&#39; deve ser precedido por uma &#39;Class&#39; correspondente
`End Class` usado para concluir uma `Class` bloco; portanto, ele só pode aparecer no final do bloco. Ou você tem um redundantes `End Class`, ou seu `End Class` instrução aparece fora dos limites de seu correspondente `Class` bloco.  
  
 **ID do erro:** BC30460  
  
### Para corrigir este erro  
  
-   Localize e remova qualquer `End Class` instruções.  
  
-   Mova o `End Class` instrução para o local apropriado em seu código.  
  
## Consulte também  
 [Instrução End \<keyword\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)