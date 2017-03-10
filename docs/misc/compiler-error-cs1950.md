---
title: "CS1950 de erro do compilador | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1950 de erro do compilador
O melhor adicionar método sobrecarregado 'name' para o inicializador de coleção tem alguns argumentos inválidos.  
  
 Para oferecer suporte inicializadores de coleção, uma classe deve implementar IEnumerable e ter um público `Add` método. Para inicializar o tipo usando um inicializador de coleção, o parâmetro de entrada de `Add` método deve ser compatível com o tipo do objeto que você está tentando adicionar.  
  
### Para corrigir este erro  
  
-   Use um tipo compatível no inicializador de coleção.  
  
-   Modificar o parâmetro de entrada e\/ou a acessibilidade do `Add` método no tipo de coleção.  
  
-   Adicione um novo `Add` método com um parâmetro de entrada que coincide com o que você está passando em.  
  
-   Tornar sua classe de coleção genérica para que ele possa ter um `Add` método que aceita qualquer tipo que você passar.  
  
## Exemplo  
 O exemplo a seguir gera CS1950:  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## Consulte também  
 [Inicializadores de objeto e coleção](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)