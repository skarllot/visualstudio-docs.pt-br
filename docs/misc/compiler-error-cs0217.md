---
title: "CS0217 de erro do compilador | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0217 de erro do compilador
Para ser aplicado como um operador de circuito pequeno, um operador lógico definido pelo usuário \('operator'\) deve ter o mesmo tipo de retorno como o tipo dos seus 2 parâmetros.  
  
 Se você definir um operador para um tipo definido pelo usuário e, em seguida, tente usar o operador como um operador de curto\-circuito, o operador definido pelo usuário deve ter parâmetros e valores de retorno do mesmo tipo. Para obter mais informações sobre curto\-circuito operadores, consulte [& & operador](/dotnet/csharp/language-reference/operators/conditional-and-operator) e [&#124; &#124; Operador](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 O exemplo a seguir gera CS0217:  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## Consulte também  
 [Operadores sobrecarregáveis](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)