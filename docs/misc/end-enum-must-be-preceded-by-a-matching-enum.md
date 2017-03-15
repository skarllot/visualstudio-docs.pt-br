---
title: "&#39;End Enum&#39; deve ser precedido por &#39;Enum&#39; correspondente | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30184"
  - "vbc30184"
helpviewer_keywords: 
  - "BC30184"
ms.assetid: b7f5ebf0-10c8-4320-8caf-dffc24ae8a71
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Enum&#39; deve ser precedido por &#39;Enum&#39; correspondente
Um `End Enum` declaração ocorre sem um correspondente `Enum` instrução.`End Enum` deve ser precedida por uma `Enum` instrução.  
  
 **ID do erro:** BC30184  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que um anterior `Enum` instrução não é escrito incorretamente ou são inválidos.  
  
2.  Verifique se o `Enum` membros estão formatados corretamente.  
  
## Consulte também  
 [Instrução Enum](/dotnet/visual-basic/language-reference/statements/enum-statement)