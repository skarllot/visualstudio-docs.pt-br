---
title: "CS0231 de erro do compilador | Microsoft Docs"
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
  - "CS0231"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0231"
ms.assetid: e5e6a8e1-6c9f-4a88-8935-7bedfba88f8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0231 de erro do compilador
Um parâmetro params deve ser o último parâmetro em uma lista de parâmetros formais.  
  
 O [params](/dotnet/csharp/language-reference/keywords/params) parâmetro oferece suporte a um número variável de argumentos e deve ser após todos os outros parâmetros. Para obter mais informações, consulte [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 O exemplo a seguir gera CS0231:  
  
```  
// CS0231.cs class Test { public void TestMethod(params int[] p, int i) {} // CS0231 // To resolve the error, use the following line instead: // public void TestMethod(int i, params int[] p) {} static void Main() { } }  
```