---
title: "CS0209 de erro do compilador | Microsoft Docs"
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
  - "CS0209"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0209"
ms.assetid: a408a869-02db-414f-97c1-bfb1637f6155
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0209 de erro do compilador
O tipo de local declarado em uma instrução fixed deve ser um tipo de ponteiro  
  
 A variável que você declara em um [instrução fixa](/dotnet/csharp/language-reference/keywords/fixed-statement) deve ser um ponteiro. Para obter mais informações, consulte [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 O exemplo a seguir gera CS0209:  
  
```  
// CS0209.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0209 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```