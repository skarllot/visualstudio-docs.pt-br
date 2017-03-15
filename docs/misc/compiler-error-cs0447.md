---
title: "CS0447 de erro do compilador | Microsoft Docs"
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
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0447 de erro do compilador
Atributos não podem ser usados em argumentos de tipo, somente em parâmetros de tipo  
  
 Esse erro ocorre quando você aplica um atributo a um argumento de tipo ocorre em uma instrução de chamada. É aceitável para aplicar um atributo a um parâmetro de tipo em uma instrução de declaração de classe ou método como o seguinte:  
  
```  
class C<[some attribute] T> {…}  
```  
  
 A linha de código a seguir gerará esse erro. Supõe\-se que a classe `C`, definido na linha de código anterior tem um método estático chamado `MyStaticMethod`.  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## Exemplo  
 O código a seguir gera erro CS0447.  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```