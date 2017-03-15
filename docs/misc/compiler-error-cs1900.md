---
title: "CS1900 de erro do compilador | Microsoft Docs"
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
  - "CS1900"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1900"
ms.assetid: 08141138-bfea-4af3-a9a0-ec54cf2caa13
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1900 de erro do compilador
Nível de aviso deve estar no intervalo de 0 a 4  
  
 O [\/ Avisar](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) opção de compilador só pode ter um dos cinco valores possíveis \(0, 1, 2, 3 ou 4\). Qualquer outro valor passado para **\/warn** resultará em CS1900.  
  
 O exemplo a seguir gera CS1900:  
  
```  
// CS1900.cs // compile with: /W:5 // CS1900 expected class x { public static void Main() { } }  
```