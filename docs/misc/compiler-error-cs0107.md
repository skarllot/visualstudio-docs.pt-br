---
title: "CS0107 de erro do compilador | Microsoft Docs"
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
  - "CS0107"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0107"
ms.assetid: 505763c5-6d68-4c57-a8bd-7b03682da4c5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0107 de erro do compilador
Mais de um modificador de proteção  
  
 Somente um modificador \([pública](/dotnet/csharp/language-reference/keywords/public), [privada](/dotnet/csharp/language-reference/keywords/private), [protegido](/dotnet/csharp/language-reference/keywords/protected), ou [interno](/dotnet/csharp/language-reference/keywords/internal)\) é permitido em um membro de classe, com exceção de exceto **interno protegido**.  
  
 O exemplo a seguir gera CS0107:  
  
```  
// CS0107.cs public class C { private internal void f()   // CS0107, delete private or internal { } public static int Main() { return 1; } }  
```