---
title: "CS2021 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS2021 de erro do compilador
Arquivo nome '' é muito longo ou inválido  
  
 Todos os nomes de arquivo passados para o compilador c\# devem ter menos de `_MAX_PATH` \(definido em um arquivo de cabeçalho do Windows\). o compilador fornecerá esse erro nas seguintes situações:  
  
-   Um nome de arquivo \(incluindo o caminho\) for maior que `_MAX_PATH`.  
  
-   O nome do arquivo contém caracteres inválidos.  
  
-   O nome do arquivo contém caracteres curinga onde curingas não são permitidos \(como nomes de arquivo de recurso\).