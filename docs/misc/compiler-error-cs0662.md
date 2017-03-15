---
title: "CS0662 de erro do compilador | Microsoft Docs"
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
  - "CS0662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0662"
ms.assetid: 836fa15e-3bf3-4af5-8acf-072d7d731dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0662 de erro do compilador
'method' não pode especificar somente atributo Out em um parâmetro ref. Use tanto em e atributos ou nenhum deles.  
  
 Um método de interface tem um parâmetro que usa [ref](/dotnet/csharp/language-reference/keywords/ref) com apenas o [Out](frlrfSystemRuntimeInteropServicesOutAttributeClassTopic) atributo. Um `ref` parâmetro usa o **Out** atributo também deve usar o [na](frlrfSystemRuntimeInteropServicesInAttributeClassTopic) atributo.  
  
 O exemplo a seguir gera CS0662:  
  
```  
// CS0662.cs using System.Runtime.InteropServices; interface I { void method([Out] ref int i);   // CS0662 // try one of the following lines instead // void method(ref int i); // void method([Out, In]ref int i); } class test { public static void Main() { } }  
```