---
title: "&#39;Case Else&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc30071"
  - "vbc30071"
helpviewer_keywords: 
  - "BC30071"
ms.assetid: 9a4f8ccb-717a-4d18-91b4-4a373202c38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case Else&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Select Case&#39;
Um `Case Else` declaração ocorre fora de um `Select` bloco. Um `Case Else` instrução pode ser usada somente entre um `Select` ou `Select Case` de instrução e correspondente `End Select` instrução.  
  
 **ID do erro:** BC30071  
  
### Para corrigir este erro  
  
-   Remover o `Case Else` instrução ou movê\-la para dentro de um `Select` bloco.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)