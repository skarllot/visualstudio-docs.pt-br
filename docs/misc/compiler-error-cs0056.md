---
title: "CS0056 de erro do compilador | Microsoft Docs"
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
  - "CS0056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0056"
ms.assetid: 8878b09c-5b7b-40e0-be0d-61ef5b36c151
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0056 de erro do compilador
Acessibilidade inconsistente: tipo de retorno 'type' é menos acessível que o operador 'operator'  
  
 Uma construção pública deve retornar um objeto acessível publicamente. Para obter mais informações, consulte [Modificadores de acesso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 O exemplo a seguir gera CS0056:  
  
```  
// CS0056.cs class MyClass // try the following line instead // public class MyClass { } public class A { public static implicit operator MyClass(A a)   // CS0056 { return new MyClass(); } public static void Main() { } }  
```