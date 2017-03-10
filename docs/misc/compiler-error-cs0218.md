---
title: "CS0218 de erro do compilador | Microsoft Docs"
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
  - "CS0218"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0218"
ms.assetid: f675e06a-c55c-44a1-b5db-0df178fd8f79
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0218 de erro do compilador
O tipo \('type'\) deve conter declarações de operador true e false  
  
 Se você definir um operador para um tipo definido pelo usuário e, em seguida, tente usar o operador como um operador de curto\-circuito, o operador definido pelo usuário deve ter o operador true e operador false definido. Para obter mais informações sobre curto\-circuito operadores, consulte [& & operador](/dotnet/csharp/language-reference/operators/conditional-and-operator) e [&#124; &#124; Operador](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 O exemplo a seguir gera CS0218:  
  
```  
// CS0218.cs using System; public class MyClass { // uncomment these operator declarations to resolve this CS0218 /* public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } */ public static implicit operator int(MyClass x) { return 0; } public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f;   // CS0218, requires operators true and false } }  
```  
  
## Consulte também  
 [Operadores de conversão](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators)