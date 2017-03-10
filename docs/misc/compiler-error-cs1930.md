---
title: "CS1930 de erro do compilador | Microsoft Docs"
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
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1930 de erro do compilador
A variável de intervalo 'name' já foi declarada.  
  
 A variável de intervalo em uma expressão de consulta está no escopo até que a expressão de consulta é encerrado. Portanto, ele deve ter um identificador exclusivo.  
  
### Para corrigir este erro  
  
1.  Dê um nome exclusivo para cada variável de alcance é apresentado em uma expressão de consulta.  
  
## Exemplo  
 O exemplo a seguir gera CS1930 porque o identificador `num` é usado para a variável de intervalo no `from` cláusula e para a variável de intervalo introduzidos pelo `let` cláusula.  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)