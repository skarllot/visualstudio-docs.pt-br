---
title: "&#39;Loop&#39; deve ser precedido por um &#39;Do&#39; correspondente | Microsoft Docs"
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
  - "vbc30091"
  - "bc30091"
helpviewer_keywords: 
  - "BC30091"
ms.assetid: 05f47b2f-4eaa-4911-981e-3fce737d249f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Loop&#39; deve ser precedido por um &#39;Do&#39; correspondente
Um `Loop` declaração ocorre sem um correspondente `Do` instrução.`Loop` deve ser precedida por uma `Do` instrução.  
  
 **ID do erro:** BC30091  
  
### Para corrigir este erro  
  
1.  Se este `Do` loop é parte de um conjunto de aninhada `Do` loops, verifique se cada loop termina de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `Do` loop são terminadas corretamente.  
  
3.  Certifique\-se de que isso `Do` loop está formatado corretamente.  
  
## Consulte também  
 [Instrução Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)