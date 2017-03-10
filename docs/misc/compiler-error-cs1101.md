---
title: "CS1101 de erro do compilador | Microsoft Docs"
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
  - "CS1101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1101"
ms.assetid: d6fc8834-eadf-4497-b442-0751895e6764
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1101 de erro do compilador
O modificador de parâmetro 'ref' não pode ser usado com 'this'.  
  
 Quando o `this` palavra\-chave modifica o primeiro parâmetro de um método estático, ele sinaliza ao compilador que o método é um método de extensão. Não há outros modificadores são necessárias ou permitidos no primeiro parâmetro de um método de extensão.  
  
## Exemplo  
 O exemplo a seguir gera CS1101:  
  
```  
// cs1101.cs // Compile with: /target:library public static class Extensions { // No type parameters. public static void Test(ref this int i) {} // CS1101 // Single type parameter. public static void Test<T>(ref this T t) {}// CS1101 // Multiple type parameters. public static void Test<T,U,V>(ref this U u) {}// CS1101 }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [ref](/dotnet/csharp/language-reference/keywords/ref)