---
title: "CS0023 de erro do compilador | Microsoft Docs"
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
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0023 de erro do compilador
Operador 'operator' não pode ser aplicado a operando do tipo 'type'  
  
 Foi feita uma tentativa de aplicar um operador a uma variável cujo tipo não foi projetado para trabalhar com o operador. Para obter mais informações, consulte [Tipos](/dotnet/csharp/programming-guide/types/index) e [Operadores em C\#](/dotnet/csharp/language-reference/operators/index).  
  
 O exemplo a seguir gera CS0023:  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```