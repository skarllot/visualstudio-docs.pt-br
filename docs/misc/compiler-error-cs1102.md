---
title: "CS1102 de erro do compilador | Microsoft Docs"
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
  - "CS1102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1102"
ms.assetid: 7de798d4-1b4b-4842-ae43-9bc83e6dc9a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1102 de erro do compilador
O modificador de parâmetro 'out' não pode ser usado com 'this'.  
  
 Quando o `this` palavra\-chave modifica o primeiro parâmetro de um método estático, ele sinaliza ao compilador que o método é um método de extensão. Não há outros modificadores são necessárias ou permitidos no primeiro parâmetro de um método de extensão.  
  
### Para corrigir este erro  
  
1.  Remova os modificadores não autorizados do primeiro parâmetro.  
  
## Exemplo  
 O exemplo a seguir gera CS1102:  
  
```  
// cs1102.cs // Compile with: /target:library. public static class Extensions { // No type parameters. public static void Test(this out int i) {} // CS1102 //Single type parameter public static void Test<T>(this out T t) {}// CS1102 //Multiple type parameters public static void Test<T,U,V>(this out U u) {}// CS1102 }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [out](/dotnet/csharp/language-reference/keywords/out)