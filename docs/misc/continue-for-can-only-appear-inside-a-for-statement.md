---
title: "&#39;Continue For&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;For&#39; | Microsoft Docs"
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
  - "bc30783"
  - "vbc30783"
helpviewer_keywords: 
  - "BC30783"
ms.assetid: 70891018-27c8-4d36-b168-8cc7177d70cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue For&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;For&#39;
Um `Continue For` instrução só pode aparecer dentro de uma `For...Next` loop.  
  
 **ID do erro:** BC30783  
  
### Para corrigir este erro  
  
1.  Se o `Continue For` instrução está em um `Do...Loop`, altere a instrução `Continue Do`.  
  
     – ou –  
  
     Se o `Continue For` instrução está em um `While...End While` loop, altere a instrução `Continue While`.  
  
2.  Caso contrário, remova o `Continue For` instrução.  
  
## Consulte também  
 [Instrução Continue](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)