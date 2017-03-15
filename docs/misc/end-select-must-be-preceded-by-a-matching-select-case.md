---
title: "&#39;End Select&#39; deve ser precedido por uma correspond&#234;ncia &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Select&#39; deve ser precedido por uma correspond&#234;ncia &#39;Select Case&#39;
Um `End Select` declaração ocorre sem um correspondente `Select` ou `Select Case` instrução.`End Select` deve ser precedido por um `Select` ou `Select Case` instrução.  
  
 **ID do erro:** BC30088  
  
### Para corrigir este erro  
  
1.  Se este `Select` bloco faz parte de um conjunto de aninhada `Select` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `Select` bloco são terminadas corretamente.  
  
3.  Verifique se esse `Select` bloco está formatado corretamente.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)