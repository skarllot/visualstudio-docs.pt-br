---
title: "&#39;Exit While&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;While&#39; | Microsoft Docs"
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
  - "vbc30097"
  - "bc30097"
helpviewer_keywords: 
  - "BC30097"
ms.assetid: cf0a3e09-5252-4198-bb27-c103c98d9f19
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit While&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;While&#39;
Um `Exit While` declaração ocorre fora de um `While` bloco.`Exit While` é válido somente entre uma `While` de instrução e um correspondente `End While` instrução.  
  
 **ID do erro:** BC30097  
  
### Para corrigir este erro  
  
1.  Certifique\-se de um arquivo `While` instrução precede o `Exit While` e válido `End While` instrução aparece depois.  
  
2.  Verifique se outras estruturas de controle dentro do `While` bloco são terminadas corretamente.  
  
## Consulte também  
 [Instrução While...End While](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)