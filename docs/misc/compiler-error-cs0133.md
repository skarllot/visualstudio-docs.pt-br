---
title: "CS0133 de erro do compilador | Microsoft Docs"
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
  - "CS0133"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0133"
ms.assetid: b5be456f-824d-4e6d-802b-0b1b5889efbd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0133 de erro do compilador
A expressão que está sendo atribuída a 'variável' deve ser constante  
  
 Um [const](/dotnet/csharp/language-reference/keywords/const) variável não pode tomar como seu valor de uma expressão que não é constante. Para obter mais informações, consulte [Constantes](/dotnet/csharp/programming-guide/classes-and-structs/constants).  
  
 O exemplo a seguir gera CS0133:  
  
```  
// CS0133.cs public class MyClass { public const int i = c;   // CS0133, c is not constant public static int c = i; // try the following line instead // public const int i = 6; public static void Main() { } }  
```