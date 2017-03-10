---
title: "Compilador CS0628 de aviso (n&#237;vel 4) | Microsoft Docs"
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
  - "CS0628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0628"
ms.assetid: a54cfad8-27c9-4abb-8c83-982615489a10
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0628 de aviso (n&#237;vel 4)
'member': novo membro protegido declarado na classe sealed  
  
 Um [lacrado](/dotnet/csharp/language-reference/keywords/sealed) classe não pode apresentar um [protegido](/dotnet/csharp/language-reference/keywords/protected) membro porque nenhuma outra classe poderão herdar do `sealed` da classe e usar o `protected` membro.  
  
 O exemplo a seguir gera CS0628:  
  
```  
// CS0628.cs // compile with: /W:4 sealed class C { protected int i;   // CS0628 } class MyClass { public static void Main() { } }  
```