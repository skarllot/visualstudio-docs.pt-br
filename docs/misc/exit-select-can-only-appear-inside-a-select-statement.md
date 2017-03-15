---
title: "&#39;Exit Select&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Select&#39; | Microsoft Docs"
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
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Select&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Select&#39;
Um `Exit Select` declaração ocorre fora de um `Select` bloco.`Exit Select` é válido somente entre uma `Select` ou `Select Case` de instrução e um correspondente `End Select` instrução.  
  
 **ID do erro:** BC30099  
  
### Para corrigir este erro  
  
1.  Certifique\-se de um válido `Select` ou `Select Case` instrução precede o `Exit Select` e válido `End Select` instrução aparece depois.  
  
2.  Verifique se outras estruturas de controle dentro do `Select` bloco são terminadas corretamente.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)