---
title: "CS0515 de erro do compilador | Microsoft Docs"
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
  - "CS0515"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0515"
ms.assetid: 0f8c0253-218d-4c21-b22c-fa5802ba4e7f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0515 de erro do compilador
'function': modificadores de acesso não são permitidos em construtores estáticos  
  
 Um construtor estático não pode ter um [modificador de acesso](/dotnet/csharp/language-reference/keywords/modifiers).  
  
## Exemplo  
 O exemplo a seguir gera CS0515:  
  
```  
// CS0515.cs public class Clx { public static void Main() { } } public class Clz { public static Clz()   // CS0515, remove public keyword { } }  
```