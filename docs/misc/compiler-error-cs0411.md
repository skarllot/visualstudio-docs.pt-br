---
title: "CS0411 de erro do compilador | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0411 de erro do compilador
Os argumentos de tipo para o método 'method' não podem ser inferidos do uso. Tente especificar os argumentos de tipo explicitamente.  
  
 Esse erro ocorre se você chamar um método genérico sem fornecer explicitamente os argumentos de tipo e o compilador não pode inferir destinam\-se os argumentos de tipo. Para evitar esse erro, adicione os argumentos de tipo desejado entre colchetes angulares.  
  
## Exemplo  
 O exemplo a seguir gera CS0411:  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## Exemplo  
 Outros casos de erro possível incluem quando o parâmetro for `null`, que não tem nenhuma informação de tipo:  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```