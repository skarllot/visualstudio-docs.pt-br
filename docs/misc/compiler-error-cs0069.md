---
title: "CS0069 de erro do compilador | Microsoft Docs"
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
  - "CS0069"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0069"
ms.assetid: a1b32906-7773-47c6-8515-162a201a9be5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0069 de erro do compilador
Um evento em uma interface não pode ter acessadores adicionar ou remover  
  
 Não é possível definir funções de acessador de um evento em um [interface](/dotnet/csharp/language-reference/keywords/interface). Para obter mais informações, consulte [Eventos](/dotnet/csharp/programming-guide/events/index) e [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 O exemplo a seguir gera CS0069:  
  
```  
// CS0069.cs // compile with: /target:library public delegate void EventHandler(); public interface a { event EventHandler Click { remove {} }   // CS0069 event EventHandler Click2;   // OK }  
```