---
title: "CS0265 de erro do compilador | Microsoft Docs"
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
  - "CS0265"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0265"
ms.assetid: d43d19c2-8a66-4bb1-95a0-557b0a29bce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0265 de erro do compilador
Declarações parciais de 'type' têm restrições inconsistentes para tipo de parâmetro do parâmetro' tipo'  
  
 Esse erro ocorre quando você define uma classe genérica como uma classe parcial, para que suas definições parciais ocorrem em mais de um lugar e as restrições no tipo genérico são inconsistentes ou diferentes em dois ou mais lugares. Se você especificar as restrições em mais de um único lugar, eles devem todos ser idênticos. A solução mais simples é especificar as restrições em um único lugar e omiti\-los em todos os outros. Para obter mais informações, consulte [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) e [Restrições a parâmetros de tipo](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
 O código a seguir gera erro CS0265.  
  
## Exemplo  
 Nesse código, as definições de classe parcial estão todos em um único arquivo, mas também pode ser divididos em vários arquivos.  
  
```  
// CS0265.cs public class GenericsErrors { interface IFace1 { } interface IFace2 { } partial class PartialBadBounds<T> where T : IFace1 { } // CS0265 partial class PartialBadBounds<T> where T : IFace2 { } }  
```