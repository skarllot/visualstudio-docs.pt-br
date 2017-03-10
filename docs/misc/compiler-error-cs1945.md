---
title: "CS1945 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1945"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1945"
ms.assetid: 787f61b0-4767-451c-8c78-8e456b5057eb
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1945 de erro do compilador
Uma árvore de expressão não pode conter uma expressão de método anônimo.  
  
 Árvores de expressão só podem conter expressões. Métodos anônimos podem representar apenas instruções.  
  
### Para corrigir este erro  
  
1.  Não tente criar uma árvore de expressão com uma instrução.  
  
## Exemplo  
 O código a seguir gera CS1945:  
  
```  
// cs1945.cs using System; using System.Linq.Expressions; public delegate void D(); class Test { static void Main() { Expression<Func<int, Func<int, bool>>> tree = (x => delegate(int i) { return true; }); // CS1945 } }  
```  
  
## Consulte também  
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instruções, expressões e operadores](/dotnet/csharp/programming-guide/statements-expressions-operators/index)