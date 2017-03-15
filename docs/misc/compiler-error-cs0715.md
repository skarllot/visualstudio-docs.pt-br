---
title: "CS0715 de erro do compilador | Microsoft Docs"
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
  - "CS0715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0715"
ms.assetid: e3cd1e46-ccfa-4678-a2ed-69245f3558ba
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0715 de erro do compilador
'classe estática': classes static não podem conter operadores definidos pelo usuário  
  
 Operadores definidos pelo usuário operam em instâncias de classes. Classes static não podem ser instanciadas, portanto, não é possível criar instâncias de operadores para agir. Portanto, os operadores definidos pelo usuário não são permitidas para classes estáticas.  
  
 O exemplo a seguir gera CS0715:  
  
```  
// CS0715.cs public static class C { public static C operator+(C c)  // CS0715 { } public static void Main() { } }  
```