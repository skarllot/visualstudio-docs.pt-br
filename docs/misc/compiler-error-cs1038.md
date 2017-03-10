---
title: "CS1038 de erro do compilador | Microsoft Docs"
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
  - "CS1038"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1038"
ms.assetid: 05c53ae9-2819-4771-aee8-3f2ff6bcf0b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1038 de erro do compilador
diretiva \#endregion esperada  
  
 A [\#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) diretiva não tinha uma correspondência [\#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) diretiva.  
  
 O exemplo a seguir gera CS1038:  
  
```  
// CS1038.cs #region testing public class clx { public static void Main() { } } // CS1038 // uncomment the next line to resolve // #endregion  
```