---
title: "CS1558 de erro do compilador | Microsoft Docs"
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
  - "CS1558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1558"
ms.assetid: ee603d66-007e-4782-9285-7ff031975f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1558 de erro do compilador
'class' não tem um método Main estático adequado  
  
 O [\/principal](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) opção de compilador especificada uma classe na qual procurar um **principal** método. No entanto, o [principal](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) método não foi definido corretamente.  
  
 O exemplo a seguir gera CS1558 por tipo de retorno inválido.  
  
```  
// CS1558.cs // compile with: /main:MyNamespace.MyClass namespace MyNamespace { public class MyClass { public static float Main() { return 0.0; // CS1558 because the return type is a float. } } }  
```