---
title: "N&#227;o &#233; poss&#237;vel definir o valor de uma vari&#225;vel local para um m&#233;todo que n&#227;o est&#225; na parte superior da pilha | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel definir o valor de uma vari&#225;vel local para um m&#233;todo que n&#227;o est&#225; na parte superior da pilha
Você só pode modificar variáveis se eles forem parte superior da pilha de chamadas. Por exemplo, se `procedure1` chamadas `procedure2` e você está no `procedure1`, você não pode modificar variáveis no `procedure2`.  
  
 **ID do erro:** BC30711  
  
### Para corrigir este erro  
  
-   Modificar as variáveis que estão no topo da pilha de chamadas.  
  
## Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)