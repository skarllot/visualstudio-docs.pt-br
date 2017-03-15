---
title: "CS0198 de erro do compilador | Microsoft Docs"
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
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0198 de erro do compilador
Campos de somente leitura e estático 'nome do campo' não podem ser atribuídos a \(exceto em um construtor estático ou um inicializador de variável\)  
  
 Um [readonly](/dotnet/csharp/language-reference/keywords/readonly) variável deve ter o mesmo [estático](/dotnet/csharp/language-reference/keywords/static) uso do construtor no qual você deseja inicializar. Para obter mais informações, consulte [Construtores estáticos](/dotnet/csharp/programming-guide/classes-and-structs/static-constructors).  
  
 O exemplo a seguir gera CS0198:  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```