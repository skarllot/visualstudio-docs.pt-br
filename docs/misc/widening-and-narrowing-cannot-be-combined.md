---
title: "N&#227;o n&#227;o poss&#237;vel combinar &#39;Widening&#39; e &#39;Narrowing&#39; | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o n&#227;o poss&#237;vel combinar &#39;Widening&#39; e &#39;Narrowing&#39;
Um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) especifica ambos [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) e [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 Quando você define um operador de conversão, você deve declará\-la como `Widening` ou `Narrowing`. Essas são características mutuamente, portanto, não é possível especificar ambos.  
  
 **ID do erro:** BC33001  
  
### Para corrigir este erro  
  
-   Remova o `Widening` ou o `Narrowing` palavra\-chave from a `Operator` instrução. Você deve especificar um ou outro.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)