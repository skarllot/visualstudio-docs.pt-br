---
title: "CS1002 de erro do compilador | Microsoft Docs"
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
  - "CS1002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1002"
ms.assetid: 659b7abf-9311-40c9-9594-5372464c6148
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1002 de erro do compilador
; esperado  
  
 O compilador detectou um ponto e vírgula ausente. Um ponto e vírgula em necessária no final de cada instrução em c\#. Uma instrução pode abranger mais de uma linha.  
  
 O exemplo a seguir gera CS1002:  
  
```  
// CS1002.cs namespace x { abstract public class clx { int i   // CS1002, missing semicolon public static int Main() { return 0; } } }  
```  
  
## Consulte também  
 [Instruções](/dotnet/csharp/programming-guide/statements-expressions-operators/statements)