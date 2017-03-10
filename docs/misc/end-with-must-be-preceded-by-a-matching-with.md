---
title: "&#39;End With&#39; deve ser precedido por &#39;With&#39; correspondente | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End With&#39; deve ser precedido por &#39;With&#39; correspondente
Um `End With` declaração ocorre sem um correspondente `With` instrução.`End With` deve ser precedida por uma `With` instrução.  
  
 **ID do erro:** BC30093  
  
### Para corrigir este erro  
  
1.  Se este `With` bloco faz parte de um conjunto de aninhada `With` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Verifique se outras estruturas de controle dentro do `With` bloco são terminadas corretamente.  
  
3.  Certifique\-se de que isso `With` bloco está formatado corretamente.  
  
## Consulte também  
 [Instrução With ... End With](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)