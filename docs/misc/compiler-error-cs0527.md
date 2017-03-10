---
title: "CS0527 de erro do compilador | Microsoft Docs"
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
  - "CS0527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0527"
ms.assetid: 1acd244b-c55b-424f-b038-a130d65b8685
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0527 de erro do compilador
O tipo 'type' na lista de interface não é uma interface  
  
 É possível que um [struct](/dotnet/csharp/language-reference/keywords/struct) ou [interface](/dotnet/csharp/language-reference/keywords/interface) para herdar de outra interface, mas não de qualquer outro tipo.  
  
 O exemplo a seguir gera CS0527:  
  
```  
// CS0527.cs // compile with: /target:library public struct clx : int {}   // CS0527 int not an interface  
```