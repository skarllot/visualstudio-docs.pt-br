---
title: "CS0199 de erro do compilador | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0199 de erro do compilador
Campos de somente leitura e estático 'nome do campo' não podem ser passados como ref ou out \(exceto em um construtor estático\)  
  
 Um [readonly](/dotnet/csharp/language-reference/keywords/readonly) variável deve ter o mesmo [estático](/dotnet/csharp/language-reference/keywords/static) uso do construtor no qual você deseja passar como um [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out) parâmetro. Para obter mais informações, consulte [Passando parâmetros](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Exemplo  
 O exemplo a seguir gera CS0199:  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```