---
title: "&#39;Continue While&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;While&#39; | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue While&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;While&#39;
Um `Continue While` instrução só pode aparecer dentro de uma `For...Next` loop.  
  
 **ID do erro:** BC30784  
  
### Para corrigir este erro  
  
1.  Se o `Continue While` instrução está em um `Do...Loop` loop, altere a instrução `Continue Do`.  
  
2.  Se o `Continue While` instrução está em um `For...Next` loop, altere a instrução `Continue For`.  
  
3.  Caso contrário, remova o `Continue While` instrução.  
  
## Consulte também  
 [Instrução Continue](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Instrução While...End While](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)