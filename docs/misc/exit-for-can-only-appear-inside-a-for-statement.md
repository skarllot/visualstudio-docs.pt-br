---
title: "&#39;Exit For&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;For&#39; | Microsoft Docs"
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
  - "bc30096"
  - "vbc30096"
helpviewer_keywords: 
  - "BC30096"
ms.assetid: 1062a329-9364-4234-9175-4c70a51cb7ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit For&#39; s&#243; pode aparecer dentro de uma instru&#231;&#227;o &#39;For&#39;
Um `Exit For` declaração ocorre fora de um `For` loop.`Exit For` é válido somente entre uma `For` ou `For Each` de instrução e um correspondente `Next` instrução.  
  
 **ID do erro:** BC30096  
  
### Para corrigir este erro  
  
1.  Certifique\-se de um válido `For` ou `For Each` instrução precede o `Exit For`, uma opção válida `Next` instrução aparece depois.  
  
2.  Verifique se outras estruturas de controle dentro do `For` loop são terminadas corretamente.  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Instrução For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)