---
title: "CS0457 de erro do compilador | Microsoft Docs"
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
  - "CS0457"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0457"
ms.assetid: 5d5cf762-c817-4468-9455-59e966b8c140
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0457 de erro do compilador
Ambíguo conversões definidas pelo usuário 'nome do método de conversão 1' e 'nome do método de conversão 2' durante a conversão de ' nome de tipo 1' para ' nome de tipo 2'  
  
 Dois métodos de conversão são aplicáveis, e o compilador não pode decidir qual deles usar.  
  
 Um cenário que pode causar esse erro é o seguinte:  
  
-   Você deseja converter A classe para a classe B onde A e B estão relacionados.  
  
-   Um é derivado de A0, e há um método que converte de A0 B.  
  
-   B tem uma subclasse B1 e há um método que converte de um B1.  
  
 O compilador irá ponderar os dois métodos de conversão igualmente, porque a primeira conversão fornece o melhor tipo de destino, e a segunda conversão fornece o melhor tipo de fonte. Uma vez que o compilador não poderão escolher, esse erro será gerado. Para resolver, escrever um novo método explícito convertendo A para B.  
  
 Outro cenário que causa esse erro é se há dois métodos que convertem A para B. Para corrigir, especifique qual conversão usar por meio de uma conversão explícita.  
  
## Exemplo  
 O exemplo a seguir gera CS0457.  
  
```  
// CS0457.cs using System; public class A { } public class G0 {  } public class G1<R> : G0 {  } public class H0 { public static implicit operator G0(H0 h) { return new G0(); } } public class H1<R> : H0 { public static implicit operator G1<R>(H1<R> h) { return new G1<R>(); } } public class Test { public static void F0(G0 g) {  } public static void Main() { H1<A> h1a = new H1<A>(); F0(h1a);   // CS0457 } }  
```