---
title: "CS0030 de erro do compilador | Microsoft Docs"
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
  - "CS0030"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0030"
ms.assetid: 3c9bd3f9-dea2-46dd-be1e-46c843ffd3de
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0030 de erro do compilador
Não é possível converter o tipo 'type' para 'type'  
  
 Você deve fornecer as rotinas de conversão para dar suporte a determinadas sobrecargas do operador. Para obter mais informações, consulte [Operadores de conversão](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators).  
  
 O exemplo a seguir gera CS0030:  
  
```  
// CS0030.cs namespace x { public class iii { /* public static implicit operator iii(int aa) { return null; } public static implicit operator int(iii aa) { return 0; } */ public static iii operator ++(iii aa) { return (iii)0;   // CS0030 // uncomment the conversion routines to resolve CS0030 } public static void Main() { } } }  
```