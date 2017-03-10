---
title: "&#39;Continue Do&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Do&#39; | Microsoft Docs"
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
  - "vbc30782"
  - "bc30782"
helpviewer_keywords: 
  - "BC30782"
ms.assetid: c6b35e63-4d84-449d-9685-41a1bc0a7f35
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue Do&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Do&#39;
Um `Continue Do` instrução só pode aparecer dentro de uma `Do...Loop` loop.  
  
 **ID do erro:** BC30782  
  
### Para corrigir este erro  
  
1.  Se o `Continue Do` instrução está em um `For...Next` loop, altere a instrução `Continue For`.  
  
2.  Se o `Continue Do` instrução está em um `While...End While` loop, altere a instrução `Continue While`.  
  
3.  Caso contrário, remova o `Continue Do` instrução.  
  
## Consulte também  
 [Instrução Continue](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Instrução Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)