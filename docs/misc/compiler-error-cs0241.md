---
title: "CS0241 de erro do compilador | Microsoft Docs"
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
  - "CS0241"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "valores de parâmetro do método padrão"
  - "padrões, valores de parâmetro"
  - "padrões, valores de parâmetro de método"
  - "valores de parâmetro padrão"
  - "CS0241"
ms.assetid: be31b194-3de5-4aab-b23a-6cf790f940ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0241 de erro do compilador
Não são permitidos especificadores de parâmetro padrão  
  
 [Parâmetros de método](/dotnet/csharp/language-reference/keywords/method-parameters) não podem ter valores padrão. Use sobrecargas do método para obter o mesmo efeito. Para obter mais informações, consulte [Passando parâmetros](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Exemplo  
 O exemplo a seguir gera CS0241. Além disso, o exemplo mostra como simular, com sobrecarga, um método com argumentos padrão.  
  
```  
// CS0241.cs public class A { public void Test(int i = 9) {}   // CS0241 } public class B { public void Test() { Test(9); } public void Test(int i)  {} } public class C { public static void Main() { B x = new B(); x.Test(); } }  
```