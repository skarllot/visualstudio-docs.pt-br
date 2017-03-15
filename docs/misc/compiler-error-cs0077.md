---
title: "CS0077 de erro do compilador | Microsoft Docs"
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
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0077 de erro do compilador
O operador deve ser usado com um tipo de referência ou um tipo anulável \('int' é um tipo de valor não\-nulo\).  
  
 O [como](/dotnet/csharp/language-reference/keywords/as) operador foi passado um [tipo de valor](/dotnet/csharp/language-reference/keywords/value-types). Porque `as` pode retornar [nulo](/dotnet/csharp/language-reference/keywords/null), só podem ser passada [tipos de referência](/dotnet/csharp/language-reference/keywords/reference-types) ou tipo anulável. Para obter mais informações sobre tipos anuláveis, consulte [Tipos anuláveis](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 O exemplo a seguir gera CS0077:  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```