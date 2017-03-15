---
title: "CS0261 de erro do compilador | Microsoft Docs"
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
  - "CS0261"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0261"
ms.assetid: c2af7b31-4a48-457a-8d9b-0956dd0d46f9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0261 de erro do compilador
Declarações parciais de 'type' devem ser todas as classes, structs ou interfaces  
  
 Esse erro ocorre se um tipo parcial é declarado como um tipo diferente de construção em vários lugares. Para obter mais informações, consulte [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 O exemplo a seguir gera CS0261:  
  
```  
// CS0261.cs partial class A  // CS0261 – A declared as a class here, but as a struct below { } partial struct A { }  
```