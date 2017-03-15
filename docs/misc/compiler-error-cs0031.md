---
title: "CS0031 de erro do compilador | Microsoft Docs"
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
  - "CS0031"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0031"
ms.assetid: 91f11ae9-9143-41f4-8002-5c38c8ee0651
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0031 de erro do compilador
Valor constante 'value' não pode ser convertido em 'type'. \(use sintaxe 'unchecked' para substituir\)  
  
 Foi feita uma tentativa para atribuir um valor a uma variável cujo tipo não é possível armazenar o valor. Para obter mais informações, consulte [Tipos](/dotnet/csharp/programming-guide/types/index).  
  
 O exemplo a seguir gera CS0031 em contextos marcados e desmarcados:  
  
```  
// CS0031.cs namespace CS0031 { public class a { public static void Main() { int num = (int)2147483648M; //CS0031 // Try using a larger numeric type instead: // long num = (long)2147483648M; //CS0031 const decimal d = -10M; // Decimal literal unchecked { const byte b = (byte)d; // CS0031 // For small values try using a signed byte instead: // const sbyte b = (sbyte)d; } } } }  
```  
  
## Consulte também  
 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked)