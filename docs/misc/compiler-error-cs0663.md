---
title: "CS0663 de erro do compilador | Microsoft Docs"
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
  - "CS0663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0663"
ms.assetid: 9f96c42b-dcc8-4a0f-8404-289fc88dba5e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0663 de erro do compilador
Não é possível definir métodos sobrecarregados que diferem somente em ref e out.  
  
 Métodos que diferem apenas em termos de uso [ref](/dotnet/csharp/language-reference/keywords/ref) e [out](/dotnet/csharp/language-reference/keywords/out) em um parâmetro não são permitidos.  
  
 O exemplo a seguir gera CS0663:  
  
```  
// CS0663.cs class TestClass { public static void Main() { } public void Test(ref int i) { } public void Test(out int i)   // CS0663 { } }  
```