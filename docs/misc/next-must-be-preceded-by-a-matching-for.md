---
title: "&#39;Next&#39; deve ser precedido por um &#39;For&#39; correspondente | Microsoft Docs"
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
  - "vbc30092"
  - "bc30092"
helpviewer_keywords: 
  - "BC30092"
ms.assetid: 4bf49bb2-c69b-443d-aa58-cb40fcfb1370
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; deve ser precedido por um &#39;For&#39; correspondente
Um `Next` declaração ocorre sem um correspondente `For` ou `For Each` instrução.`Next` deve ser precedida por uma `For` ou `For Each` instrução.  
  
 **ID do erro:** BC30092  
  
### Para corrigir este erro  
  
1.  Se este `For` loop é parte de um conjunto de aninhada `For` loops, verifique se cada loop termina de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `For` loop são terminadas corretamente.  
  
3.  Certifique\-se de que isso `For` loop está formatado corretamente.  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Instrução For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)