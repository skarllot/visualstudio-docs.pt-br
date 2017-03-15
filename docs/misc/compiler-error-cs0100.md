---
title: "CS0100 de erro do compilador | Microsoft Docs"
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
  - "CS0100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0100"
ms.assetid: b49e4846-2a82-48ed-9ca8-953eb5c1baaa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0100 de erro do compilador
O parâmetro nome 'nome do parâmetro' é uma duplicata  
  
 Uma declaração de método usado o mesmo nome de parâmetro mais de uma vez. Nomes de parâmetro devem ser exclusivos em uma declaração de método. Para obter mais informações, consulte [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 O exemplo a seguir gera CS0100:  
  
```  
// CS0100.cs namespace x { public class a { public static void f(int i, char i)   // CS0100 // try the following line instead // public static void f(int i, char j) { } public static void Main() { } } }  
```