---
title: "CS0180 de erro do compilador | Microsoft Docs"
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
  - "CS0180"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0180"
ms.assetid: a21bf0a2-ed5a-4ddd-88d3-240babc5888a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0180 de erro do compilador
'member' não pode ser externo e abstrato  
  
 O [abstrato](/dotnet/csharp/language-reference/keywords/abstract) e [extern](/dotnet/csharp/language-reference/keywords/extern) palavras\-chave são mutuamente exclusivas. O `extern` palavra\-chave significa que o membro é definido fora do arquivo, e **abstrato** significa que a implementação é fornecida em uma classe derivada. Para obter mais informações, consulte [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 O exemplo a seguir gera CS0180:  
  
```  
// CS0180.cs namespace MyNamespace { public class MyClass { public extern abstract int Foo(int a);   // CS0180 public static void Main() { } } }  
```