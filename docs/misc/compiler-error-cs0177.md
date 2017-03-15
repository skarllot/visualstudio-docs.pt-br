---
title: "CS0177 de erro do compilador | Microsoft Docs"
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
  - "CS0177"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0177"
ms.assetid: 852a8c2a-2411-4800-af7c-4c572d9900d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0177 de erro do compilador
O parâmetro de saída 'parâmetro' deve ser atribuído ao antes controle saia do método atual  
  
 Um parâmetro marcado com o [out](/dotnet/csharp/language-reference/keywords/out) palavra\-chave não foi atribuído um valor no corpo do método. Para obter mais informações, consulte [Passando parâmetros](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
 O exemplo a seguir gera CS0177:  
  
```  
// CS0177.cs public class MyClass { public static void Foo(out int i)   // CS0177 { // uncomment the following line to resolve this error //   i = 0; } public static void Main() { int x = -1; Foo(out x); } }  
```