---
title: "CS0745 de erro do compilador | Microsoft Docs"
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
  - "CS0745"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0745"
ms.assetid: 6ae77eb2-a940-43aa-a198-3042d144613a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0745 de erro do compilador
Palavra\-chave contextual 'por' esperada  
  
 O padrão para o `group` cláusula é `group...by` seguido de um recurso opcional `into`, conforme mostrado no exemplo a seguir:  
  
```  
string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name by name[0];  
```  
  
 ou  
  
```  
var query2 = from name in names group name by name[0] into g //...additional query clauses  
```  
  
### Para corrigir este erro  
  
1.  Adicionar o `by` palavra\-chave para o `group` cláusula.  
  
## Exemplo  
 O código a seguir gera CS0745:  
  
```  
// cs0745.cs using System; using System.Linq; public class C { public static int Main() { string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name name[0]; // CS0745 return 1; } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [Cláusula group](/dotnet/csharp/language-reference/keywords/group-clause)