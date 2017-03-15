---
title: "CS2024 de erro do compilador | Microsoft Docs"
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
  - "CS2023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2024"
ms.assetid: 65cf7419-a5a6-4128-88af-176dc8dba14f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS2024 de erro do compilador
Seção de arquivo inválido '\#' número de alinhamento  
  
 Um valor inválido foi passado para o [\/filealign](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option) opção de compilador.  
  
 O exemplo a seguir gera CS2024:  
  
```  
// CS2024.cs // compile with: /filealign:ex // CS2024 expected class MyClass { public static void Main() { } }  
```