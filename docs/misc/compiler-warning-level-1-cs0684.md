---
title: "Compilador CS0684 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0684"
ms.assetid: d6c8aaf6-c1cf-4c0e-b367-4c3e418d8bc4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0684 de aviso (n&#237;vel 1)
a interface 'interface' marcada com 'CoClassAttribute' não está marcada com 'ComImportAttribute'  
  
 Se você especificar **CoClassAttribute** em uma interface, você também deve especificar **ComImportAttribute**.  
  
 O exemplo a seguir gera CS0684:  
  
```  
// CS0684.cs // compile with: /W:1 using System; using System.Runtime.InteropServices; [CoClass(typeof(C))] // CS0684 // try the following line instead // [CoClass(typeof(C)), ComImport] interface I { } class C { static void Main() {} }  
```