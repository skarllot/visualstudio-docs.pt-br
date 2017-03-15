---
title: "CS0766 de erro do compilador | Microsoft Docs"
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
  - "CS0766"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0766"
ms.assetid: 4574e30b-3e76-42cd-90e8-31c72126a08c
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0766 de erro do compilador
Métodos parciais devem ter um tipo de retorno void.  
  
 Um método parcial não pode retornar um valor. Seu tipo de retorno deve ser nulo.  
  
### Para corrigir este erro  
  
1.  Dê o método parcial de um tipo de retorno void, caso contrário, converta o método de um método \(não parcial\) regular.  
  
## Exemplo  
 O exemplo a seguir gera CS0766:  
  
```  
// cs0766.cs using System; public partial class C { partial int Part(); // CS0766 // Typically the implementing declaration // is contained in a separate file. partial int Part() //CS0766 { } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)