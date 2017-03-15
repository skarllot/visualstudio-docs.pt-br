---
title: "CS0837 de erro do compilador | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0837 de erro do compilador
O primeiro operando de um "é" ou "como" operador não pode ser uma expressão lambda ou um método anônimo.  
  
 Métodos anônimos e expressões lambda não podem ser usados no lado esquerdo da [é](/dotnet/csharp/language-reference/keywords/is) ou [como](/dotnet/csharp/language-reference/keywords/as).  
  
### Para corrigir este erro  
  
-   Se o erro envolve o `is` operador, lembre\-se de que `is` usa um valor e um tipo e informa se o valor pode ser transformado em desse tipo por referência, conversão boxing e unboxing conversão. Porque lambdas não são valores e não tem nenhuma referência, conversão boxing e unboxing conversões, lambdas não são candidatos para `is`.  
  
-   Se o uso indevido de código `as`, a correção é provavelmente alterá\-la para uma conversão.  
  
## Exemplo  
 O exemplo a seguir gera CS0837:  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```