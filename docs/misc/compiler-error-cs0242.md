---
title: "CS0242 de erro do compilador | Microsoft Docs"
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
  - "CS0242"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0242"
ms.assetid: bc86a5a4-89c1-4de4-a874-4dd4cbf592c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0242 de erro do compilador
A operação em questão não está definida nos ponteiros void  
  
 Incrementar um ponteiro nulo não é permitido. Para obter mais informações, consulte [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 O exemplo a seguir gera CS0242:  
  
```  
// CS0242.cs // compile with: /unsafe class TestClass { public unsafe void Test() { void * p = null; p++;   // CS0242, incrementing a void pointer not allowed } public static void Main() { } }  
```