---
title: "CS0170 de erro do compilador | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0170 de erro do compilador
Uso de campo possivelmente não atribuído 'field'  
  
 Um campo em uma estrutura foi usado sem primeiro sendo inicializado. Para resolver esse problema, primeiro determine qual campo foi inicializado e inicialize\-o antes de tentar acessá\-lo. Para obter mais informações sobre como inicializar as estruturas, consulte [Structs](/dotnet/csharp/programming-guide/classes-and-structs/structs) e [Usando structs](/dotnet/csharp/programming-guide/classes-and-structs/using-structs).  
  
 O exemplo a seguir gera CS0170:  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```