---
title: "CS0070 de erro do compilador | Microsoft Docs"
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
  - "CS0070"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0070"
ms.assetid: bb0de7c6-c734-4a8f-ab62-0a50eac2a91f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0070 de erro do compilador
O evento 'event' só pode aparecer à esquerda de \+ \= ou \-\= \(exceto quando usado de dentro do tipo 'type'\)  
  
 Fora da classe é definida em, uma [evento](/dotnet/csharp/language-reference/keywords/event) só pode adicionar ou subtrair referências. Para obter mais informações, consulte [Eventos](/dotnet/csharp/programming-guide/events/index).  
  
 O exemplo a seguir gera CS0070:  
  
```  
// CS0070.cs using System; public delegate void EventHandler(); public class A { public event EventHandler Click; public static void OnClick() { EventHandler eh; A a = new A(); eh = a.Click; } public static void Main() { } } public class B { public int Foo () { EventHandler eh = new EventHandler(A.OnClick); A a = new A(); eh = a.Click;   // CS0070 // try the following line instead // a.Click += eh; return 1; } }  
```