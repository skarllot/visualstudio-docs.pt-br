---
title: "&#39;If&#39; deve finalizar com &#39;End If&#39; correspondente | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; deve finalizar com &#39;End If&#39; correspondente
Um `If` declaração ocorre sem um correspondente `End If` instrução. Um `End If` declaração deve ser usada para encerrar o `If` bloco.  
  
 **ID do erro:** BC30081  
  
### Para corrigir este erro  
  
1.  Se este `If` bloco faz parte de um conjunto de aninhada `If` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Adicione um `End If` instrução ao final do `If` bloco.  
  
## Consulte também  
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)