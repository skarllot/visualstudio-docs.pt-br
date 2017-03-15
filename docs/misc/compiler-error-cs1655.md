---
title: "CS1655 de erro do compilador | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1655 de erro do compilador
Não é possível passar campos de 'variável' como ref ou out argumento porque ele é um 'readonly tipo de variável'  
  
 Esse erro ocorre se você estiver tentando passar um membro de um [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) variável, um [usando](/dotnet/csharp/language-reference/keywords/using-statement) variável, ou um [fixo](/dotnet/csharp/language-reference/keywords/fixed-statement) variável para uma função como ref ou out argumento. Como essas variáveis são consideradas somente leitura nesses contextos, isso não é permitido.  
  
 O exemplo a seguir gera CS1655:  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```