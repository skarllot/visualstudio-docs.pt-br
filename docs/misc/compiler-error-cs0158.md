---
title: "CS0158 de erro do compilador | Microsoft Docs"
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
  - "CS0158"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0158"
ms.assetid: 88ac61a9-ce55-4272-9141-0873765a7034
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0158 de erro do compilador
O rótulo 'Rótulo' Sombra de outro rótulo com o mesmo nome em um escopo contido  
  
 Um rótulo em um escopo interno oculta um rótulo com o mesmo nome em um escopo externo. Para obter mais informações, consulte [goto](/dotnet/csharp/language-reference/keywords/goto).  
  
 O exemplo a seguir gera CS0158:  
  
```  
// CS0158.cs namespace MyNamespace { public class MyClass { public static void Main() { goto lab1; lab1: { lab1: goto lab1;   // CS0158 } } } }  
```