---
title: "CS1551 de erro do compilador | Microsoft Docs"
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
  - "CS1551"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1551"
ms.assetid: 09fde2a2-7466-418a-88ef-395321358b07
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1551 de erro do compilador
Indexadores devem ter pelo menos um parâmetro  
  
 Um [indexador](/dotnet/csharp/programming-guide/indexers/index) que leva nenhum argumento foi declarado.  
  
 O exemplo a seguir gera CS1551:  
  
```  
// CS1551.cs public class MyClass { int intI; int this[]   // CS1551 // try the following line instead // int this[int i] { get { return intI; } set { intI = value; } } public static void Main() { } }  
```