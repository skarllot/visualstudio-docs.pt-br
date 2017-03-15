---
title: "CS1947 de erro do compilador | Microsoft Docs"
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
  - "CS1947"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1947"
ms.assetid: e2822fba-a176-4466-9cdc-63c44e22ebcb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1947 de erro do compilador
A variável de intervalo 'nome da variável' não pode ser atribuída a \- \-é somente leitura.  
  
 Uma variável de alcance é como uma variável de iteração em uma `foreach` instrução. Ele não pode ser atribuído a uma expressão de consulta.  
  
### Para corrigir este erro  
  
1.  Remova a atribuição à variável de intervalo.  
  
2.  Se necessário, introduza uma nova variável de intervalo usando o `let` cláusula e usá\-lo para armazenar o valor.  
  
## Exemplo  
 O código a seguir gera CS1947:  
  
```  
// cs1947.cs using System.Linq; class Test { static void Main() { int[] array = new int[] { 1, 2, 3, 4, 5 }; var x = from i in array let k = i select i = 5; // CS1947 x.ToList(); } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)