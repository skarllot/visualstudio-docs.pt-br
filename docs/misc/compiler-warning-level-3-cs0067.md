---
title: "Compilador CS0067 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS0067"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0067"
ms.assetid: df75220b-0b93-45ec-8655-98d9333b0bb7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0067 de aviso (n&#237;vel 3)
O evento 'event' nunca é usado  
  
 Um [evento](/dotnet/csharp/language-reference/keywords/event) foi declarada mas nunca foi usada na classe na qual ela foi declarada.  
  
 O exemplo a seguir gera CS0067:  
  
```  
// CS0067.cs // compile with: /W:3 using System; delegate void MyDelegate(); class MyClass { public event MyDelegate evt;   // CS0067 // uncomment TestMethod to resolve this CS0067 /* private void TestMethod() { if (evt != null) evt(); } */ public static void Main() { } }  
```