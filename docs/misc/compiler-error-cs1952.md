---
title: "CS1952 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1952"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1952"
ms.assetid: 8c560bf9-df93-40f5-a3d8-c66b31cde08f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1952 de erro do compilador
Uma árvore de expressão lambda não pode conter um método com argumentos de variável  
  
 O suporte `__arglist` palavra\-chave não é permitido em expressões lambda compiladas em árvores de expressão.  
  
### Para corrigir este erro  
  
1.  Se esqueça de que você já ouviu falar do `__arglist`.  
  
## Exemplo  
 O código a seguir produz CS1952:  
  
```  
// cs1952.cs using System; using System.Linq.Expressions; class Test { public static int M(__arglist) { return 1; } static int Main() { Expression<Func<int, int>> f = x => Test.M(__arglist(x)); // CS1952 return 1; } }  
  
```