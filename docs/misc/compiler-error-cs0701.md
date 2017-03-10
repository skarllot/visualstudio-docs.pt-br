---
title: "CS0701 de erro do compilador | Microsoft Docs"
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
  - "CS0701"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0701"
ms.assetid: eb844e31-00bd-468d-9f77-11d10a4ef120
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0701 de erro do compilador
'identifier' não é uma restrição válida. Um tipo usado como uma restrição deve ser uma interface, uma classe não selada ou um parâmetro de tipo.  
  
 Esse erro ocorre se um tipo lacrado é usado como uma restrição. Para resolver esse erro, use somente os tipos não lacrados como restrições.  
  
## Exemplo  
 O exemplo a seguir gera CS0701.  
  
```  
// CS0701.cs // compile with: /target:library class C<T> where T : System.String {}   // CS0701 class D<T> where T : System.Attribute {}   // OK  
```