---
title: "Compilador CS1030 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1030"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1030"
ms.assetid: 7c565abc-1366-4641-9383-ab8ba026ab96
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1030 de aviso (n&#237;vel 1)
\#warning: 'texto'  
  
 Exibe o texto de um aviso definido com o [\#warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-warning) diretiva.  
  
 O exemplo a seguir mostra como criar um aviso definido pelo usuário:  
  
```  
// CS1030.cs class Sample { static void Main() { #warning Let's give a warning here   // CS1030 } }  
```