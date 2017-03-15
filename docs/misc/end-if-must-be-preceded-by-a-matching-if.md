---
title: "&#39;End If&#39; deve ser precedido por &#39;If&#39; correspondente | Microsoft Docs"
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
  - "bc30087"
  - "vbc30087"
helpviewer_keywords: 
  - "BC30087"
ms.assetid: 81c056bb-267e-44ef-9a44-3a41273090ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End If&#39; deve ser precedido por &#39;If&#39; correspondente
Um `End If` declaração ocorre sem um correspondente `If` instrução.`End If` deve ser precedido por um `If` instrução.  
  
 **ID do erro:** BC30087  
  
### Para corrigir este erro  
  
1.  Se este `If` bloco faz parte de um conjunto de aninhada `If` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `If` bloco são terminadas corretamente.  
  
3.  Certifique\-se de que isso `If` bloco está formatado corretamente.  
  
## Consulte também  
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)