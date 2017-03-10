---
title: "CS1940 de erro do compilador | Microsoft Docs"
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
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1940 de erro do compilador
Várias implementações do padrão de consulta foram encontradas para o tipo de origem 'type'. Chamada ambígua para 'method'.  
  
 Esse erro é gerado quando várias implementações de um método de consulta são definidas e o compilador não pode resolver a ambiguidade de qual delas é melhor usar para a consulta. No exemplo a seguir, ambas as versões do `Select` tem a mesma assinatura, porque ambos aceitarem um `int` como um parâmetro de entrada e `int` como um valor de retorno.  
  
### Para corrigir este erro  
  
1.  Fornece apenas uma implementação para cada método.  
  
## Exemplo  
 O código a seguir gera CS1940:  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## Consulte também  
 [Visão geral de operadores de consulta padrão](../Topic/Standard%20Query%20Operators%20Overview.md)