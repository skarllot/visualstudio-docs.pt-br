---
title: "CS1530 de erro do compilador | Microsoft Docs"
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
  - "CS1530"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1530"
ms.assetid: 3844b5ef-e0ec-42df-9267-72689020f128
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1530 de erro do compilador
Palavra\-chave 'new' não é permitida em elementos definidos em um namespace  
  
 Não é necessário especificar o [novo](/dotnet/csharp/language-reference/keywords/new) palavra\-chave em qualquer construção que está em uma [namespace](/dotnet/csharp/language-reference/keywords/namespace).  
  
 O exemplo a seguir gera CS1530:  
  
```  
// CS1530.cs namespace a { new class i   // CS1530 { } // try the following instead class ii { public static void Main() { } } }  
```