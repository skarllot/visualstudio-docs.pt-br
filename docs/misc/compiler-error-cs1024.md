---
title: "CS1024 de erro do compilador | Microsoft Docs"
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
  - "CS1024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1024"
ms.assetid: 41f587cb-1958-4eb6-9f8d-c03500e55e21
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1024 de erro do compilador
Diretiva de pré\-processamento esperada  
  
 Início de uma linha com o símbolo de sustenido \(\#\), mas a cadeia de caracteres subseqüente não era válido [diretiva de pré\-processador](/dotnet/csharp/language-reference/preprocessor-directives/index).  
  
 O exemplo a seguir gera CS1024:  
  
```  
// CS1024.cs #import System   // CS1024  
```