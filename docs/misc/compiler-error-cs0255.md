---
title: "CS0255 de erro do compilador | Microsoft Docs"
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
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0255 de erro do compilador
stackalloc não pode ser usada em uma variável ou bloco finally  
  
 O [stackalloc](/dotnet/csharp/language-reference/keywords/stackalloc) palavra\-chave não pode ser usada em uma [catch](/dotnet/csharp/language-reference/keywords/try-catch) ou [Finalmente](/dotnet/csharp/language-reference/keywords/try-catch-finally) bloco. Para obter mais informações, consulte [Exceções e manipulação de exceções](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 O exemplo a seguir gera CS0255:  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```