---
title: "CS1025 de erro do compilador | Microsoft Docs"
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
  - "CS1025"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1025"
ms.assetid: 491c186f-cb40-47a9-9656-44fadfa18ae2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1025 de erro do compilador
Comentário de linha única ou final de linha esperado  
  
 Uma linha com um [diretiva de pré\-processador](/dotnet/csharp/language-reference/preprocessor-directives/index) não pode ter um comentário de várias linhas.  
  
 O exemplo a seguir gera CS1025:  
  
```  
#if true /* hello */   // CS1025 #endif   // this is a good comment  
```  
  
 CS1025 também pode ocorrer se você tentar fazer alguma diretiva de pré\-processador inválida, da seguinte maneira:  
  
```  
// CS1025.cs #define a class Sample { static void Main() { #if a 1   // CS1025, invalid syntax System.Console.WriteLine("Hello, World!"); #endif } }  
```