---
title: "CS0742 de erro do compilador | Microsoft Docs"
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
  - "CS0742"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0742"
ms.assetid: 078ee7af-17e4-4572-8fee-d97e09c9002b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0742 de erro do compilador
Corpo de uma consulta deve terminar com uma cláusula select ou group  
  
 Uma expressão de consulta deve terminar com um uma `select` cláusula ou um `group` cláusula sem uma continuação.  
  
### Para corrigir este erro  
  
1.  Adicione um [cláusula select](/dotnet/csharp/language-reference/keywords/select-clause) ou [cláusula group](/dotnet/csharp/language-reference/keywords/group-clause) à consulta.  
  
## Exemplo  
 O código a seguir gera CS0742:  
  
```  
// cs0742.cs using System.Linq; public class Test { public static int Main() { int[] array = { 1, 2, 3 }; var query = from num in array; // CS0742 return 1; } }  
```  
  
 Se o `group` cláusula usa a [em](/dotnet/csharp/language-reference/keywords/into) palavra\-chave para armazenar os resultados do agrupamento em um identificador temporário, ele não pode ser a última cláusula em uma consulta. Um `select` ou segundo `group` cláusula ainda é necessária.  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)