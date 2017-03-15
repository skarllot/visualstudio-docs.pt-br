---
title: "CS0743 de erro do compilador | Microsoft Docs"
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
  - "CS0743"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0743"
ms.assetid: 0dc8040a-a12f-4da6-9ed0-c0284905ee83
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0743 de erro do compilador
Palavra\-chave contextual 'on' esperado  
  
 O padrão para um `join` cláusula é `join`...`in`...`on`...`equals`, conforme mostrado neste exemplo:  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### Para corrigir este erro  
  
1.  Adicionar o `on` palavra\-chave para o `join` cláusula.  
  
## Exemplo  
 O código a seguir gera CS0743:  
  
```  
// cs0743.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 x equals y // CS0743 select x; return 1; } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [Cláusula join](/dotnet/csharp/language-reference/keywords/join-clause)