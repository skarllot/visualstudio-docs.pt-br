---
title: "CS0074 de erro do compilador | Microsoft Docs"
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
  - "CS0074"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0074"
ms.assetid: 9395c532-3934-4553-8e41-042bfe3399ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0074 de erro do compilador
'event': evento abstract não pode ter inicializador  
  
 Se um [evento](/dotnet/csharp/language-reference/keywords/event) está marcado como **abstrato**, ele não pode ser inicializado. Para obter mais informações, consulte [Eventos](/dotnet/csharp/programming-guide/events/index).  
  
 O exemplo a seguir gera CS0074:  
  
```  
// CS0074.cs delegate void D(); abstract class Test { public abstract event D e = null;   // CS0074 // try the following line instead // public abstract event D e; public static void Main() { } }  
```