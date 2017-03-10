---
title: "CS0149 de erro do compilador | Microsoft Docs"
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
  - "CS0149"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0149"
ms.assetid: c3c0e48e-8dba-4ee6-86fd-cbb02c68255c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0149 de erro do compilador
Nome de método esperado  
  
 Ao criar um [Delegar](/dotnet/csharp/language-reference/keywords/delegate), especificar um método. Para obter mais informações, consulte [Delegados](/dotnet/csharp/programming-guide/delegates/index).  
  
 O exemplo a seguir gera CS0149:  
  
```  
// CS0149.cs using System; delegate string MyDelegate(int i); class MyClass { // class member-field of the declared delegate type static MyDelegate dt; public static void Main() { dt = new MyDelegate(17.45);   // CS0149 // try the following line instead // dt = new MyDelegate(Func2); F(dt); } public static string Func2(int j) { Console.WriteLine(j); return j.ToString(); } public static void F(MyDelegate myFunc) { myFunc(8); } }  
```