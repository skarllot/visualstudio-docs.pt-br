---
title: "&#39;Finally&#39; n&#227;o pode aparecer fora &#39;Try&#39; instru&#231;&#227;o | Microsoft Docs"
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
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; n&#227;o pode aparecer fora &#39;Try&#39; instru&#231;&#227;o
`Finally` usado para concluir uma `Try...Catch...Finally` bloco; portanto ele pode aparecer apenas uma vez no final do bloco. Ou você tem um desnecessários `Finally`, ou seu `Finally` instrução aparece fora dos limites de seu correspondente `Try` bloco.  
  
 **ID do erro:** BC30382  
  
### Para corrigir este erro  
  
1.  Localize e remova os desnecessários `Finally`instrução.  
  
2.  Mova o `Finally` instrução para o local apropriado em seu código.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Tratamento de visão geral do Visual Basic de exceções estruturado](http://msdn.microsoft.com/pt-br/bb81af80-a735-4873-9711-6151a48e418a)