---
title: "CS1601 de erro do compilador | Microsoft Docs"
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
  - "CS1601"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1601"
ms.assetid: 5efa1d2d-c70c-446d-a51f-d23d8a3be22e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1601 de erro do compilador
Parâmetro delegate ou método não pode ser do tipo 'type'  
  
 Alguns tipos na biblioteca de classes do .NET Framework, por exemplo, <xref:System.TypedReference>, <xref:System.RuntimeArgumentHandle> e <xref:System.ArgIterator> não pode ser usado como [ref](/dotnet/csharp/language-reference/keywords/ref) ou [out](/dotnet/csharp/language-reference/keywords/out) parâmetros porque eles potencialmente podem ser usados para executar operações não seguras.  
  
 O exemplo a seguir gera CS1601:  
  
```  
// CS1601.cs using System; class MyClass { public void Test1 (ref TypedReference t)   // CS1601 { } public void Test2 (out ArgIterator t)   // CS1601 { } }  
```