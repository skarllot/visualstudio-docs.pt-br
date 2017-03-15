---
title: "CS0452 de erro do compilador | Microsoft Docs"
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
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0452 de erro do compilador
O tipo 'type name' deve ser um tipo de referência para usá\-lo como parâmetro de nome do parâmetro no tipo ou método 'identificador genérico de genérico'  
  
 Esse erro ocorre quando você passa um tipo de valor, como um `struct` ou `int` como um parâmetro para um tipo ou método genérico que tem uma restrição de tipo de referência.  
  
## Exemplo  
 O código a seguir gera erro CS0452.  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## Consulte também  
 [Restrições a parâmetros de tipo](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)