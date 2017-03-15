---
title: "CS0225 de erro do compilador | Microsoft Docs"
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
  - "CS0225"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0225"
ms.assetid: 0b0cd72b-c47a-44d1-9b27-d1a1fad06807
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0225 de erro do compilador
O parâmetro params deve ser uma matriz dimensional única  
  
 Ao usar o [params](/dotnet/csharp/language-reference/keywords/params) palavra\-chave, você deve especificar uma matriz unidimensional do tipo de dados. Para obter mais informações, consulte [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Exemplo  
 O exemplo a seguir gera CS0225:  
  
```  
// CS0225.cs public class MyClass { public static void TestParams(params int a)   // CS0225 // try the following line instead // public static void TestParams(params int[] a) { } public static void Main() { TestParams(1); } }  
```