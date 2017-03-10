---
title: "Erro MSB1012 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.MissingResponseFileError"
helpviewer_keywords: 
  - "MSB1012"
ms.assetid: 6e09e21d-9f64-4a8c-adec-f8efb28b7ac2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1012 (MSBuild)
**Especifique um arquivo de resposta.**  
  
 Um arquivo de resposta deve ser especificado para o @ comutador.  
  
### Para corrigir este erro  
  
-   Especifique um arquivo de resposta. A sintaxe é @\< nome do arquivo \>, por exemplo, `@BuildHW.txt`  
  
-   Não inclua o @ comutador na linha de comando.  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)