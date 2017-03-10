---
title: "CS0191 de erro do compilador | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0191 de erro do compilador
Propriedade ou indexador 'name' não pode ser atribuído a \-\-é somente leitura  
  
 Um [readonly](/dotnet/csharp/language-reference/keywords/readonly) campo só pode ter uma atribuição em um construtor ou declaração. Para obter mais informações, consulte [Construtores](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 CS0191 também ocorrerá se o `readonly` campo é [estático](/dotnet/csharp/language-reference/keywords/static) e não está marcado como o construtor `static`.  
  
## Exemplo  
 O exemplo a seguir gera CS0191.  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```