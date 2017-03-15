---
title: "CS0453 de erro do compilador | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0453 de erro do compilador
O tipo 'Type Name' deve ser um tipo de valor não nulo para usá\-lo como o parâmetro 'Nome do parâmetro' no tipo genérico ou método 'Identificador genérico'  
  
 Esse erro ocorre quando você usa um argumento de tipo de valor não instanciar um tipo genérico ou método que tem o **value** restrição nele. Ele também pode ocorrer quando você usa um argumento de tipo de valor anulável. Consulte as duas últimas linhas de código no exemplo a seguir.  
  
## Exemplo  
 O código a seguir gera este erro.  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```