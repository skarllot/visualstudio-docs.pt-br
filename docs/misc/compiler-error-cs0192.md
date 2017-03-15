---
title: "CS0192 de erro do compilador | Microsoft Docs"
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
  - "CS0192"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0192"
ms.assetid: d3fb6d18-dbf3-42c3-a280-afe55b97c2d1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0192 de erro do compilador
Campos de somente leitura e estático 'nome do campo' não podem ser passados como ref ou out \(exceto em um construtor estático\)  
  
 Um campo \(variável\) é marcado com o [readonly](/dotnet/csharp/language-reference/keywords/readonly) palavra\-chave não pode ser passado para um [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out) parâmetro exceto dentro de um construtor. Para obter mais informações, consulte [Campos](/dotnet/csharp/programming-guide/classes-and-structs/fields).  
  
 CS0192 também ocorrerá se o `readonly` campo é [estático](/dotnet/csharp/language-reference/keywords/static) e não está marcado como o construtor `static`.  
  
## Exemplo  
 O exemplo a seguir gera CS0192.  
  
```  
// CS0192.cs class MyClass { public readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // OK } public void PassReadOnlyRef() { TestMethod(ref TestInt);   // CS0192 } public static void Main() { } }  
```