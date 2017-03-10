---
title: "CS1951 de erro do compilador | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1951 de erro do compilador
Uma árvore de expressão lambda não pode conter um out ou ref parâmetro.  
  
 Uma árvore de expressão representa apenas expressões como estruturas de dados. Não há nenhuma maneira de representar locais de memória específica é necessária quando você passa um parâmetro por referência.  
  
### Para corrigir este erro  
  
1.  A única opção é remover o `ref` modificador na definição de delegado e passe o parâmetro por valor.  
  
## Exemplo  
 O exemplo a seguir gera CS1951:  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## Consulte também  
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)