---
title: "CS1929 de erro do compilador | Microsoft Docs"
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
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1929 de erro do compilador
Argumento de instância: não é possível converter de 'typeA' em 'typeB'.  
  
 Esse erro é gerado quando você tentar chamar um método de extensão de uma classe que não estende. No exemplo mostrado aqui, o método de extensão é definido para a classe derivada `A`, mas não para a classe base `B`.  
  
### Para corrigir este erro  
  
1.  Crie um novo método de extensão para o tipo em que você precisa chamá\-la, caso contrário, mova a chamada em um objeto do tipo que estende o método existente.  
  
## Exemplo  
 O código a seguir gera CS1928 e CS1929:  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)