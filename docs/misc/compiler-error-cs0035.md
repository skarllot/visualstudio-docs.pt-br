---
title: "CS0035 de erro do compilador | Microsoft Docs"
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
  - "CS0035"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0035"
ms.assetid: a622113e-98a4-4583-992c-1fb55139320a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0035 de erro do compilador
Operador 'operator' é ambíguo em um operando do tipo 'type'  
  
 O compilador tem mais de uma conversão disponível e não sabe qual escolher antes de aplicar o operador. Para obter mais informações, consulte [Conversões definidas pelo usuário com modelo](../misc/templated-user-defined-conversions.md) e [Operadores de conversão](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators).  
  
 O exemplo a seguir gera CS0035:  
  
```  
// CS0035.cs class MyClass { private int i; public MyClass(int i) { this.i = i; } public static implicit operator double(MyClass x) { return (double) x.i; } public static implicit operator decimal(MyClass x) { return (decimal) x.i; } } class MyClass2 { static void Main() { MyClass x = new MyClass(7); object o = - x;   // CS0035 // try a cast: // object o = - (double)x; } }  
  
```