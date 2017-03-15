---
title: "CS0263 de erro do compilador | Microsoft Docs"
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
  - "CS0263"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0263"
ms.assetid: 94fe3eb0-10e9-4602-a993-68fe125c8565
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0263 de erro do compilador
Declarações parciais de 'type' não devem especificar classes base diferentes  
  
 Ao definir um tipo em declarações parciais, especifique os mesmos tipos de base em cada uma das declarações parciais. Para obter mais informações, consulte [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 O exemplo a seguir gera CS0263:  
  
```  
  
// CS0263.cs // compile with: /target:library class B1 { } class B2 { } partial class C : B1  // CS0263 – is the base class B1 or B2? { } partial class C : B2 { }  
```