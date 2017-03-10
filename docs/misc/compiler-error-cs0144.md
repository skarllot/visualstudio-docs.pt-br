---
title: "CS0144 de erro do compilador | Microsoft Docs"
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
  - "CS0144"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0144"
ms.assetid: 3904cab1-05bd-44ec-81d0-e36c5656f742
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0144 de erro do compilador
Não é possível criar uma instância da classe abstrata ou interface 'interface'  
  
 Não é possível criar uma instância de um [abstrato](/dotnet/csharp/language-reference/keywords/abstract) classe ou um [interface](/dotnet/csharp/language-reference/keywords/interface). Para obter mais informações, consulte [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 O exemplo a seguir gera CS0144:  
  
```  
// CS0144.cs interface MyInterface { } public class MyClass { public static void Main() { MyInterface myInterface = new MyInterface ();   // CS0144 } }  
```