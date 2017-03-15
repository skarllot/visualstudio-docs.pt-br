---
title: "&#39;Exit Do&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Do&#39; | Microsoft Docs"
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
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Do&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;Do&#39;
Um `Exit Do` declaração ocorre fora de um `Do` loop.`Exit Do` é válido somente entre uma `Do` de instrução e um correspondente `Loop` instrução.  
  
 **ID do erro:** BC30089  
  
### Para corrigir este erro  
  
1.  Certifique\-se de um arquivo `Do` instrução precede o `Exit Do` e válido `Loop` instrução aparece depois.  
  
2.  Verifique se outras estruturas de controle dentro do `Do` loop são terminadas corretamente.  
  
## Consulte também  
 [Instrução Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)