---
title: "CS1528 de erro do compilador | Microsoft Docs"
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
  - "CS1528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1528"
ms.assetid: 38aabc5c-b32f-4bea-a585-c4212f42751d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1528 de erro do compilador
Esperado; ou \= \(não é possível especificar argumentos de construtor na declaração\)  
  
 Uma referência a uma classe foi formada como se um objeto para a classe que está sendo criado. Por exemplo, houve uma tentativa para passar uma variável para um construtor. Use o [novo](/dotnet/csharp/language-reference/keywords/new) operador para criar um objeto de uma classe.  
  
 O exemplo a seguir gera CS1528:  
  
```  
// CS1528.cs using System; public class B { public B(int i) { _i = i; } public void PrintB() { Console.WriteLine(_i); } private int _i; } public class mine { public static void Main() { B b(3);   // CS1528, reference is not an object // try one of the following // B b; // or // B bb = new B(3); // bb.PrintB(); } }  
```