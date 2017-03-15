---
title: "CS1013 de erro do compilador | Microsoft Docs"
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
  - "CS1013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1013"
ms.assetid: e5b1d24d-e558-4f7c-b2b1-3a644710005d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1013 de erro do compilador
Número inválido  
  
 O compilador detectou um número incorreto. Para obter mais informações sobre tipos integrais, consulte o [Tabela de tipos integrais](/dotnet/csharp/language-reference/keywords/integral-types-table).  
  
## Exemplo  
 O exemplo a seguir gera CS1013:  
  
```  
// CS1013.cs class Sample { static void Main() { int i = 0x;   // CS1013 } }  
```