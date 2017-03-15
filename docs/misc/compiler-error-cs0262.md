---
title: "CS0262 de erro do compilador | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0262 de erro do compilador
Declarações parciais de 'type' têm modificadores de acessibilidade conflitantes  
  
 Esse erro ocorre se um tipo parcial tem modificadores inconsistentes como público, privado, protegido, interno ou abstrato. Esses modificadores devem ser consistentes em todas as declarações parciais para esse tipo. Para obter mais informações, consulte [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
## Exemplo  
 O exemplo a seguir gera CS0262:  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```