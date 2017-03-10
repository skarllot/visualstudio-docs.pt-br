---
title: "CS1509 de erro do compilador | Microsoft Docs"
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
  - "CS1509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1509"
ms.assetid: 51a475c3-f085-49cb-89b0-c6582b68653f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1509 de erro do compilador
Arquivo referenciado 'arquivo' não é um assembly. Use ' \/ \/addmodule ' opção  
  
 Um arquivo de saída \(arquivo de saída 1\), produzido em uma compilação usada [\/target: Module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) \(não tem um manifesto de assembly\), foi especificado para [\/Reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option). Portanto, em vez de acrescentar um assembly para o assembly para o programa atual, as informações de metadados no arquivo de saída 1 serão adicionadas ao assembly para o programa atual.