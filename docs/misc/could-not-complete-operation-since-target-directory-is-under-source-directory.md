---
title: "N&#227;o foi poss&#237;vel concluir a opera&#231;&#227;o pois o diret&#243;rio de destino est&#225; sob o diret&#243;rio de origem | Microsoft Docs"
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
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o foi poss&#237;vel concluir a opera&#231;&#227;o pois o diret&#243;rio de destino est&#225; sob o diret&#243;rio de origem
Uma operação cíclica falhou. Ciclo de operações cíclicas e, portanto, não é possível concluir. Por exemplo, um objeto pode tentar herdar do objeto B, que por sua vez herda do objeto A.  
  
### Para corrigir este erro  
  
-   Quando herdar, certifique\-se de que não há nenhuma referência cíclica.  
  
## Consulte também  
 [Tipos de erro](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/pt-br/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)