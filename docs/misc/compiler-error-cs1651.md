---
title: "CS1651 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1651 de erro do compilador
Campos de somente leitura e estático 'Identificador de campo' não podem ser passados como ref ou out \(exceto em um construtor estático\)  
  
 Esse erro ocorre se você passar uma variável para uma função que é um membro de um campo somente leitura estático como um argumento ref. Como parâmetros ref podem ser modificados pela função, isso não é permitido. Para resolver esse erro, remova o **readonly** palavra\-chave no campo ou fazer não passe os membros de readonly campo para a função. Por exemplo, você poderá tentar criar um temporário variável que pode ser modificado e passando o temporário como um argumento ref, conforme mostrado no exemplo a seguir.  
  
 O exemplo a seguir gera CS1651:  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```