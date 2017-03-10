---
title: "CS0132 de erro do compilador | Microsoft Docs"
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
  - "CS0132"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0132"
ms.assetid: e8ad1281-2912-4b6a-b2af-a319a23ddd16
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0132 de erro do compilador
'construtor': um construtor estático não deve ter parâmetro  
  
 Um [estático](/dotnet/csharp/language-reference/keywords/static) construtor não pode ser declarado com um ou mais parâmetros. Para obter mais informações, consulte [Construtores](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 O exemplo a seguir gera CS0132:  
  
```  
// CS0132.cs namespace MyNamespace { public class MyClass { public MyClass(int i) { } } public class MyClass2 : MyClass { static MyClass2(int i)   // CS0132 { } } }  
```