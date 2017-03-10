---
title: "CS0538 de erro do compilador | Microsoft Docs"
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
  - "CS0538"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0538"
ms.assetid: 46ac205e-16b0-4637-bd0f-9a755ac19f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0538 de erro do compilador
'name' na declaração de interface explícita não é uma interface  
  
 Foi feita uma tentativa para declarar explicitamente uma [interface](/dotnet/csharp/language-reference/keywords/interface), mas não foi especificada uma interface.  
  
 O exemplo a seguir gera CS0538:  
  
```  
// CS0538.cs interface MyIFace { void F(); } public class MyClass { public void G() { } } class C: MyIFace { void MyIFace.F() { } void MyClass.G()   // CS0538, MyClass not an interface { } }  
```