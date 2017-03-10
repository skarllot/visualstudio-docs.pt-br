---
title: "CS1043 de erro do compilador | Microsoft Docs"
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
  - "CS1043"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1043"
ms.assetid: 749703a1-d8ac-4be6-9c48-753f64ae92a1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1043 de erro do compilador
{ou; esperado  
  
 Um acessador de propriedade foi declarado incorretamente. Para obter mais informações, consulte [Usando propriedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemplo  
 O exemplo a seguir gera CS1043.  
  
```  
// CS1043.cs // compile with: /target:library public class MyClass { public int DoSomething { get return 1;   // CS1043 set {} } // OK public int DoSomething2 { get { return 1;} } }  
```