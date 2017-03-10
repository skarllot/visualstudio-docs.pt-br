---
title: "CS0754 de erro do compilador | Microsoft Docs"
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
  - "CS0754"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0754"
ms.assetid: c83e04b5-6ab5-45c2-805e-0ba4f041d506
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0754 de erro do compilador
Um método parcial não pode implementar explicitamente um método de interface.  
  
 Um método parcial não pode ser declarado como uma implementação explícita de um método definido em uma interface.  
  
### Para corrigir este erro  
  
1.  Remova a qualificação de interface explícita da declaração de método.  
  
## Exemplo  
 O código a seguir gera CS0754:  
  
```  
// cs0754.cs using System; public interface IF { void Part(); } public partial class C : IF { partial void IF.Part(); //CS0754 public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Implementação de interface explícita](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)   
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)