---
title: "CS1542 de erro do compilador | Microsoft Docs"
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
  - "CS1542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1542"
ms.assetid: d7f60aa2-6645-472c-ac12-fa57a09fbd87
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1542 de erro do compilador
'dll' não pode ser adicionado a este assembly porque já é um assembly. Use ' \/ R' opção  
  
 O arquivo que foi referenciado com o [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) opção de compilador não foi criada com [\/target: Module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md); use [\/Reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) para referenciar o arquivo nesta compilação.