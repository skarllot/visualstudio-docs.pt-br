---
title: "CS0307 de erro do compilador | Microsoft Docs"
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
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0307 de erro do compilador
O identificador' 'em construção' ' não é um método genérico. Se você pretende obter uma lista de expressões, use parênteses em torno de \< expressão.  
  
 A chamada de construção não era um tipo ou um método, as construções únicas que pode levar a argumentos genéricos. Remova os argumentos de tipo entre colchetes angulares. Se for necessário um genérico, declare sua construção genérica como um tipo genérico ou método.  
  
 O exemplo a seguir gera CS0307:  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```