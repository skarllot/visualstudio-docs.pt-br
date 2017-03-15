---
title: "&#39;End While&#39; deve ser precedido por um &#39;While&#39; correspondente | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End While&#39; deve ser precedido por um &#39;While&#39; correspondente
Um `End While` declaração ocorre sem um correspondente `While` instrução.`End While` deve ser precedida por uma `While` instrução.  
  
 **ID do erro:** BC30090  
  
### Para corrigir este erro  
  
1.  Se este `While` bloco faz parte de um conjunto de aninhada `While` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `While` bloco são terminadas corretamente.  
  
3.  Certifique\-se de que isso `While` bloco está formatado corretamente.  
  
## Consulte também  
 [Instrução While...End While](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)