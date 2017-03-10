---
title: "Instru&#231;&#245;es e r&#243;tulos n&#227;o s&#227;o v&#225;lidos entre &#39;Select Case&#39; e primeiro &#39;Case&#39; | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es e r&#243;tulos n&#227;o s&#227;o v&#225;lidos entre &#39;Select Case&#39; e primeiro &#39;Case&#39;
Uma instrução que não é um comentário aparece entre a abertura `Select` ou `Select Case` instrução e a sua primeira `Case` instrução.  
  
 **ID do erro:** BC30058  
  
### Para corrigir este erro  
  
-   Se a instrução interveniente for um comentário, preceda com um comentário delimitador \(`'` ou `REM`\). Caso contrário, mova ou exclua a instrução.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)