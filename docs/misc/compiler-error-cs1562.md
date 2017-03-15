---
title: "CS1562 de erro do compilador | Microsoft Docs"
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
  - "CS1562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1562"
ms.assetid: fbadbcc6-9cf2-4af6-b372-fd4e4da4402e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1562 de erro do compilador
Saídas sem origem devem ter a opção \/out especificada  
  
 A compilação foi possível criar um arquivo de saída, mas não havia nenhum arquivo de código fonte como entrada do qual o nome do arquivo de saída pode ser implícito. Por exemplo, você pode estar tentando compilar um arquivo ou recurso\-somente de metadados.  
  
 Use o [\/out](/dotnet/csharp/language-reference/compiler-options/out-compiler-option) opção de compilador para especificar o nome do arquivo de saída.