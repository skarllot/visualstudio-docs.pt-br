---
title: "CS1517 de erro do compilador | Microsoft Docs"
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
  - "CS1517"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1517"
ms.assetid: 3b0201fb-8fab-4e6a-9ad9-f04c0de89517
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1517 de erro do compilador
Expressão de pré\-processamento inválida  
  
 O compilador encontrou uma expressão de pré\-processamento inválida.  
  
 Para obter mais informações, consulte [diretivas do pré\-processador](/dotnet/csharp/language-reference/preprocessor-directives/index).  
  
 O exemplo a seguir mostra algumas expressões de pré\-processador válidas e inválidas:  
  
```  
// CS1517.cs #if symbol      // OK #endif #if !symbol     // OK #endif #if (symbol)    // OK #endif #if true        // OK #endif #if false       // OK #endif #if 1           // CS1517 #endif #if ~symbol     // CS1517 #endif #if *           // CS1517 #endif class x { public static void Main() { } }  
```