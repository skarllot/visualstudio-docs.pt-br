---
title: "CS1012 de erro do compilador | Microsoft Docs"
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
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1012 de erro do compilador
Número excessivo de caracteres no literal de caractere  
  
 Foi feita uma tentativa para inicializar um [char](/dotnet/csharp/language-reference/keywords/char) constante com mais de um caractere.  
  
 CS1012 também pode ocorrer ao fazer a ligação de dados. Por exemplo, a linha a seguir fornecerá um erro:  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 Tente em vez disso, a seguinte linha:  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 O exemplo a seguir gera CS1012:  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```