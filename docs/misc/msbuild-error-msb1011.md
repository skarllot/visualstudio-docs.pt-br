---
title: "Erro MSB1011 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1011 (MSBuild)
**Especifique o arquivo de projeto ou solução usar porque esta pasta contém mais de um arquivo de projeto ou solução.**  
  
 Se um arquivo de projeto não for especificado na linha de comando, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] procura no diretório de trabalho atual para um arquivo que tem uma extensão de arquivo que termina em "proj" ou "sln" e usa esse arquivo. O diretório de trabalho atual contém mais de um arquivo que tem uma extensão de arquivo que termina em "proj" ou "sln".  
  
### Para corrigir este erro  
  
1.  Inclua o nome do arquivo de projeto na linha de comando. Por exemplo, em vez de digitar `msbuild`, tipo `msbuild myapp.proj`.  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)