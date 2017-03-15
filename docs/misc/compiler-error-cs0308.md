---
title: "CS0308 de erro do compilador | Microsoft Docs"
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
  - "CS0308"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0308"
ms.assetid: b52ef9d2-f5b3-4baf-9a7e-bb1371e79463
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0308 de erro do compilador
O método não genérico tipo\-ou\-'identifier' não pode ser usado com argumentos de tipo.  
  
 O tipo ou método não é genérico, mas foi usado com argumentos de tipo. Para evitar esse erro, remova os colchetes angulares e argumentos de tipo ou redeclarar o método ou tipo como tipo ou método genérico.  
  
 O exemplo a seguir gera CS0308:  
  
```  
// CS0308a.cs class MyClass { public void F() {} public static void Main() { F<int>();  // CS0308 – F is not generic. // Try this instead: // F(); } }  
```  
  
 O exemplo a seguir também gera CS0308. Para resolver o erro, use a diretiva "using System.Collections.Generic".  
  
```  
// CS0308b.cs // compile with: /t:library using System.Collections; // To resolve, uncomment the following line: // using System.Collections.Generic; public class MyStack<T> { // Store the elements of the stack: private T[] items = new T[100]; private int stack_counter = 0; // Define the iterator block: public IEnumerator<T> GetEnumerator()   // CS0308 { for (int i = stack_counter - 1 ; i >= 0; i--) yield return items[i]; } }  
  
```