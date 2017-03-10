---
title: "CS0765 de erro do compilador | Microsoft Docs"
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
  - "CS0765"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0765"
ms.assetid: adfb1f95-f7b1-4e43-83c2-42e8531eb980
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0765 de erro do compilador
Métodos parciais com apenas uma declaração de definição ou métodos condicionais removidos não podem ser usados em árvores de expressão  
  
 Embora uma chamada para um método parcial removido é uma expressão, não é uma expressão aceitável em uma árvore de expressão.  
  
### Para corrigir este erro  
  
1.  Adicione uma declaração de implementação para o método parcial ou remover o código que está causando o método a ser excluído da compilação condicional.  
  
## Exemplo  
 O código a seguir gera CS0765 em dois locais:  
  
```  
// cs0765.cs using System; using System.Collections; using System.Collections.Generic; using System.Diagnostics; using System.Linq; using System.Linq.Expressions; public delegate void dele(); public class ConClass { [Conditional("CONDITION")] public static void TestMethod() { } } public partial class PartClass : IEnumerable { List<object> list = new List<object>(); partial void Add(int x); public IEnumerator GetEnumerator() { for (int i = 0; i < list.Count; i++) yield return list[i]; } static void Main() { Expression<Func<PartClass>> testExpr1 = () => new PartClass { 1, 2 }; // CS0765 Expression<dele> testExpr2 = () => ConClass.TestMethod(); // CS0765 } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)