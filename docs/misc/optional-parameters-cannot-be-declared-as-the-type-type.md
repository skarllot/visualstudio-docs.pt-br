---
title: "Par&#226;metros opcionais n&#227;o podem ser declarados como o tipo &#39;&lt; type &gt;&#39; | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros opcionais n&#227;o podem ser declarados como o tipo &#39;&lt; type &gt;&#39;
Parâmetros opcionais não podem ser do tipo de dados de uma estrutura.  
  
 **ID do erro:** BC30423  
  
### Para corrigir este erro  
  
1.  Para passar uma estrutura para um parâmetro opcional, declare o parâmetro como `Object`.  
  
2.  Use `CType` para converter o parâmetro para esse tipo de estrutura dentro do procedimento.  
  
## Consulte também  
 [Estruturas e classes](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)