---
title: "CS1922 de erro do compilador | Microsoft Docs"
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
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1922 de erro do compilador
Inicializador de coleção requer seu tipo 'type' para implementar System.Collections.IEnumerable.  
  
 Para usar um inicializador de coleção com um tipo, o tipo deve implementar `IEnumerable`. Esse erro pode ocorrer se você acidentalmente usar sintaxe do inicializador de coleção quando você pretende usar um inicializador de objeto.  
  
### Para corrigir este erro  
  
-   Se o tipo não representa uma coleção, use a sintaxe do inicializador de objeto, em vez de sintaxe do inicializador de coleção.  
  
-   Se o tipo representam uma coleção, modificá\-lo para implementar `IEnumerable` antes de poder usar os inicializadores de coleção para inicializar objetos desse tipo.  
  
-   Se o tipo representa uma coleção e você não tem acesso ao código\-fonte, basta inicialize seus elementos usando seus construtores de classe ou outros métodos de inicialização.  
  
## Exemplo  
 O código a seguir produz CS1922:  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## Consulte também  
 [Inicializadores de objeto e coleção](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)