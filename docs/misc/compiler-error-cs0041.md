---
title: "CS0041 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0041"
ms.assetid: 80dbfe00-8cdb-4275-9574-8a215c7139d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0041 de erro do compilador
O nome totalmente qualificado para 'type' é muito longo para informações de depuração. Compilar sem opção '\/debug'.  
  
 Esse erro pode ocorrer ao usar o [\/Debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) opção de compilador. Se você encontrar esse erro, tente excluir os arquivos PDB no diretório bin e recompilar. Se você ainda estiver encontrando esse erro, você talvez precise reparar ou reinstalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].