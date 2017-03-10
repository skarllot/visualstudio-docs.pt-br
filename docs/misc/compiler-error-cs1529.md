---
title: "CS1529 de erro do compilador | Microsoft Docs"
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
  - "CS1529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1529"
ms.assetid: 672a6fd1-3a1f-422c-a29f-46f196d15211
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1529 de erro do compilador
Uso de uma cláusula deve preceder todos os outros elementos definidos no namespace, exceto declarações de alias extern  
  
 Um [usando](/dotnet/csharp/language-reference/keywords/using) cláusula deve aparecer primeira em um namespace.  
  
## Exemplo  
 O exemplo a seguir gera CS1529:  
  
```  
// CS1529.cs namespace X { namespace Subspace { using Microsoft; class SomeClass { }; using Microsoft;      // CS1529, place before class definition } using System.Reflection;  // CS1529, place before namespace 'Subspace' } using System;                 // CS1529, place at the beginning of the file  
```