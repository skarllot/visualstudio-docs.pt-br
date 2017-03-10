---
title: "&#39;Case&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Select Case&#39; | Microsoft Docs"
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
  - "vbc30072"
  - "bc30072"
helpviewer_keywords: 
  - "BC30072"
ms.assetid: da808bc3-f154-444a-b547-3cf55beff8a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Select Case&#39;
Um `Case` declaração ocorre fora de um `Select` bloco. Um `Case` instrução pode ser usada somente entre um `Select` ou `Select Case` de instrução e correspondente `End Select` instrução.  
  
 **ID do erro:** BC30072  
  
### Para corrigir este erro  
  
-   Remover o `Case` instrução ou movê\-la para dentro de um `Select` bloco.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)