---
title: "CS0744 de erro do compilador | Microsoft Docs"
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
  - "CS0744"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0744"
ms.assetid: 7ce430d6-737a-4103-9116-d9a4a69f8af3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0744 de erro do compilador
Palavra\-chave contextual esperada 'equals'  
  
 O padrão para um `join` cláusula é `join`...`in`...`on`...`equals`, conforme mostrado neste exemplo:  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### Para corrigir este erro  
  
1.  Adicionar o `equals` palavra\-chave para o `join` cláusula.  
  
## Exemplo  
 O código a seguir gera CS0744:  
  
```  
// cs0744.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 on x y // CS0744 select x; return 1; } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [Cláusula join](/dotnet/csharp/language-reference/keywords/join-clause)