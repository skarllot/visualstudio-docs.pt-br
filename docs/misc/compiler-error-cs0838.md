---
title: "CS0838 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0838"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0838"
ms.assetid: 22495e47-3331-42ef-921c-f76ff03ef1f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0838 de erro do compilador
Uma árvore de expressão não pode conter um inicializador de matriz multidimensional.  
  
 Matrizes multidimensionais em árvores de expressão não podem ser inicializados usando um inicializador de matriz.  
  
### Para corrigir este erro  
  
1.  Criar e inicializar a matriz antes de criar a árvore de expressão.  
  
## Exemplo  
 O exemplo a seguir gera CS0838:  
  
```  
// cs0838.cs using System; using System.Linq; using System.Linq.Expressions; namespace TestNamespace { class Test { static int Main() { Expression<Func<int[,]>> expr = () => new int[2, 2] { { 1, 2 }, { 3, 4 } }; // CS0838 // try the following 2 lines instead int[,] nums = new int[2, 2] { { 1, 2 }, { 3, 4 } }; Expression<Func<int[,]>> expr2 = () => nums; return 1; } } }  
  
```  
  
## Consulte também  
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)