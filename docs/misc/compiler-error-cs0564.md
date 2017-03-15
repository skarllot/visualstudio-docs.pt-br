---
title: "CS0564 de erro do compilador | Microsoft Docs"
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
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0564 de erro do compilador
O primeiro operando de um operador de deslocamento sobrecarregado deve ter o mesmo tipo do tipo recipiente e o tipo do segundo operando deve ser int  
  
 Você tentou sobrecarregar um operador de deslocamento \(\<\< ou \>\>\) com operandos digitados incorretamente. O primeiro operando deve ser do tipo e o segundo operando deve ser do tipo `int`.  
  
 O exemplo a seguir gera CS0564:  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```