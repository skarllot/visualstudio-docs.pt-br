---
title: "CS0210 de erro do compilador | Microsoft Docs"
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
  - "CS0210"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0210"
ms.assetid: 9f2ec1b8-6ca4-4147-b004-e3b43e7e8754
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0210 de erro do compilador
Você deve fornecer um inicializador em uma declaração de instrução fixed ou using  
  
 Você deve declarar e inicializar a variável em uma [instrução fixa](/dotnet/csharp/language-reference/keywords/fixed-statement). Para obter mais informações, consulte [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 O exemplo a seguir gera CS0210:  
  
```  
// CS0210a.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0210 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```  
  
 O exemplo a seguir também gera CS0210 porque o [usando a instrução](/dotnet/csharp/language-reference/keywords/using-statement) não tem nenhum inicializador.  
  
```  
// CS0210b.cs using System.IO; class Test { static void Main() { using (StreamWriter w) // CS0210 // Try this line instead: // using (StreamWriter w = new StreamWriter("TestFile.txt")) { w.WriteLine("Hello there"); } } }  
```