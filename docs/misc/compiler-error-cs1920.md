---
title: "CS1920 de erro do compilador | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1920 de erro do compilador
O inicializador de elemento não pode estar vazio.  
  
 Um inicializador de coleção consiste em uma seqüência de inicializadores de elemento. Os inicializadores de elemento não precisa ser colocado entre chaves, a menos que contenham uma expressão de atribuição. No entanto, se você fornecer chaves, eles não podem estar vazios. Se o inicializador de elemento é um inicializador de objeto, as chaves podem estar vazias como o inicializador contém uma nova expressão de criação de objeto.  
  
### Para corrigir este erro  
  
-   Adicione a expressão ausente entre as chaves.  
  
-   Se a expressão deve ser um inicializador de objeto, adicione a nova expressão de criação de objeto na frente de chaves.  
  
## Exemplo  
 O exemplo a seguir gera CS1920:  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## Consulte também  
 [Inicializadores de objeto e coleção](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)