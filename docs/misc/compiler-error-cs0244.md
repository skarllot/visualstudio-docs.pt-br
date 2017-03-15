---
title: "CS0244 de erro do compilador | Microsoft Docs"
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
  - "CS0244"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0244"
ms.assetid: f10e4479-ed6e-40dc-9fab-914e404d7f84
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0244 de erro do compilador
Não 'is' nem 'as' é válido em tipos de ponteiro  
  
 O [é](/dotnet/csharp/language-reference/keywords/is) e [como](/dotnet/csharp/language-reference/keywords/as) palavras\-chave não são válidas para uso em tipos de ponteiro. Para obter mais informações, consulte [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 O exemplo a seguir gera CS0244:  
  
```  
// CS0244.cs // compile with: /unsafe class UnsafeTest { unsafe static void SquarePtrParam (int* p) { bool b = p is object;   // CS0244 p is pointer } unsafe public static void Main() { int i = 5; SquarePtrParam (&i); } }  
```