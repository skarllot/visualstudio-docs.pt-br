---
title: "&#39;Else&#39; deve ser precedido por um &#39;If&#39; ou &#39;ElseIf&#39; correspondente | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Else&#39; deve ser precedido por um &#39;If&#39; ou &#39;ElseIf&#39; correspondente
Um `Else` declaração ocorre sem um correspondente `If` instrução.`Else` deve ser precedido por um `If` instrução.  
  
 **ID do erro:** BC30086  
  
### Para corrigir este erro  
  
1.  Se este `If` bloco faz parte de um conjunto de aninhada `If` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `If` bloco são terminadas corretamente.  
  
3.  Certifique\-se de que isso `If` bloco está formatado corretamente.  
  
## Consulte também  
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)