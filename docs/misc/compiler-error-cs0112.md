---
title: "CS0112 de erro do compilador | Microsoft Docs"
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
  - "CS0112"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0112"
ms.assetid: 6741c7c4-8553-4bbe-b950-4f908e8d9ba3
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0112 de erro do compilador
Um membro estático 'function' não pode ser marcado como override, virtual ou abstract  
  
 Qualquer declaração de método que usa o `override`, **virtual**, ou **abstrato** palavra\-chave também não pode usar o **estático** palavra\-chave.  
  
 Para obter mais informações, consulte [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 O exemplo a seguir gera CS0112:  
  
```  
// CS0112.cs namespace MyNamespace { abstract public class MyClass { public abstract void Foo(); } public class MyClass2 : MyClass { override public static void Foo()   // CS0112, remove static keyword { } public static int Main() { return 0; } } }  
```