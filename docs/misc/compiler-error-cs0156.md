---
title: "CS0156 de erro do compilador | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0156 de erro do compilador
Uma instrução throw sem argumentos não é permitida em um finalmente a cláusula que está aninhada em delimitador mais próximo de cláusula catch  
  
 Um [Lançar](/dotnet/csharp/language-reference/keywords/throw) instrução sem parâmetros só pode aparecer em uma **catch** cláusula sem parâmetros.  
  
 Para obter mais informações, consulte [instruções de tratamento de exceção](/dotnet/csharp/language-reference/keywords/exception-handling-statements) e [Exceções e manipulação de exceções](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 O exemplo a seguir gera CS0156:  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```