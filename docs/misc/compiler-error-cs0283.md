---
title: "CS0283 de erro do compilador | Microsoft Docs"
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
  - "CS0283"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0283"
ms.assetid: f94a5b84-92c5-4602-894d-6f856d57e0e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0283 de erro do compilador
O tipo 'type' não pode ser declarado const  
  
 O tipo especificado em uma declaração constante deve ser `byte`, `char`, `short`, `int`, `long`, `float`, `double`, `decimal`, `bool`, `string`, um tipo enum ou um tipo de referência é atribuído um valor nulo. Cada expressão de constante deve produzir um valor do tipo de destino ou de um tipo que possa ser convertido para o tipo de destino por conversão implícita.  
  
## Exemplo  
 O exemplo a seguir gera CS0283.  
  
```  
// CS0283.cs struct MyTest { } class MyClass { // To resolve the error but retain the "const-ness", // change const to readonly. const MyTest test = new MyTest();   // CS0283 public static int Main() { return 1; } }  
```