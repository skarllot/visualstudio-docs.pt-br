---
title: "CS1106 de erro do compilador | Microsoft Docs"
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
  - "CS1106"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1106"
ms.assetid: 3585600a-6b2c-47aa-a418-ef049f07c107
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1106 de erro do compilador
Métodos de extensão devem ser definidos em uma classe estática não genérica.  
  
 Métodos de extensão devem ser definidos como métodos estáticos em uma classe estática não genérica.  
  
## Exemplo  
 O exemplo a seguir gera CS1106 porque a classe `Extensions` não está definido como `static`:  
  
```  
// cs1106.cs public class Extensions // CS1106 { public  static void Test<T>(this System.String s) {} }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [static](/dotnet/csharp/language-reference/keywords/static)