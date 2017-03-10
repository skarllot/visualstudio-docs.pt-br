---
title: "&#39;Exit Try&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30393"
  - "bc30393"
helpviewer_keywords: 
  - "BC30393"
ms.assetid: b8651df3-a32f-478c-a6d8-aa0ef584155f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Try&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Try&#39;
`Exit Try` só pode aparecer dentro de uma `Try` Bloco de instrução. Ou você tem um redundantes `Exit Try` instrução, ou seu `Exit Try` instrução aparece fora dos limites de seu correspondente `Try` bloco.  
  
 **ID do erro:** BC30393  
  
### Para corrigir este erro  
  
1.  Localize e remova os desnecessários `Exit Try` instrução.  
  
2.  Mova o `Exit Try`instrução até o local apropriado em seu código.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Tratamento de visão geral do Visual Basic de exceções estruturado](http://msdn.microsoft.com/pt-br/bb81af80-a735-4873-9711-6151a48e418a)