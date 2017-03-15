---
title: "CS0622 de erro do compilador | Microsoft Docs"
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
  - "CS0622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0622"
ms.assetid: aef77a69-d8b7-41f8-9539-258deaef5cc4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0622 de erro do compilador
Só pode usar expressões de inicializador de matriz para atribuir a tipos de matriz. Tente usar uma nova expressão.  
  
 Foi usada sintaxe apropriada inicializar uma matriz na declaração de não\-matriz.  
  
## Exemplo  
 O exemplo a seguir gera CS0622:  
  
```  
// CS0622.cs using System; public class Test { public static void Main () { Test t = { new Test() };   // CS0622 // Try the following instead: // Test[] t = { new Test() }; } }  
```