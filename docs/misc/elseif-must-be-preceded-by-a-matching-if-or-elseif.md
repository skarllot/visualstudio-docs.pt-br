---
title: "&#39;ElseIf&#39; deve ser precedido por um &#39;If&#39; ou &#39;ElseIf&#39; correspondente | Microsoft Docs"
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
  - "bc36005"
  - "vbc36005"
helpviewer_keywords: 
  - "BC36005"
ms.assetid: bcebae85-b438-4839-bada-2f8f8dcc8a86
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ElseIf&#39; deve ser precedido por um &#39;If&#39; ou &#39;ElseIf&#39; correspondente
Um `ElseIf` declaração ocorre sem um correspondente `If` instrução.`ElseIf` deve ser precedido por um `If` instrução ou outro `ElseIf` instrução.  
  
 **ID do erro:** BC36005  
  
### Para corrigir este erro  
  
1.  Se este `If` bloco faz parte de um conjunto de estruturas de controle aninhadas, certifique\-se de cada estrutura é encerrada corretamente.  
  
2.  Verifique se outras estruturas de controle aninhadas dentro dessa `If` bloco são terminadas corretamente.  
  
3.  Certifique\-se de que isso `If` bloco está formatado corretamente.  
  
## Consulte também  
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Estruturas de decisão](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)