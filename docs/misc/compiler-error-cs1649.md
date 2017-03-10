---
title: "CS1649 de erro do compilador | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1649 de erro do compilador
Membros de somente leitura 'Identificador de campo' não podem ser passados como ref ou out \(exceto em um construtor\)  
  
 Esse erro ocorre se você passar uma variável para uma função que é membro de um `readonly` campo como um `ref` ou `out` argumento. Como `ref` e `out` parâmetros podem ser modificados pela função, isso não é permitido. Para resolver esse erro, remova o `readonly` palavra\-chave no campo, ou não passe os membros do `readonly` campo para a função. Por exemplo, você poderá tentar criar um temporário variável que pode ser modificado e passando temporário como um `ref` argumento, conforme mostrado no exemplo a seguir.  
  
## Exemplo  
 O exemplo a seguir gera CS1649:  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```