---
title: "CS1027 de erro do compilador | Microsoft Docs"
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
  - "CS1027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1027"
ms.assetid: a6657f0f-5664-47a5-95cf-803f5a0e0c90
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1027 de erro do compilador
Diretiva \#endif esperada  
  
 Uma correspondência `#endif` [diretiva de pré\-processador](/dotnet/csharp/language-reference/preprocessor-directives/index) não foi encontrado para um `#if` diretiva.  Ou, o compilador pode ter encontrado um `#endregion` diretiva quando não havia nenhuma correspondência `#region` diretiva dentro de um `#if` bloco.  
  
 O exemplo a seguir gera CS1027:  
  
```  
// CS1027.cs #if true   // CS1027, uncomment next line to resolve // #endif namespace x { public class clx { public static void Main() { } } }  
```