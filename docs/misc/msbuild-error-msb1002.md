---
title: "Erro MSB1002 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1002 (MSBuild)
**Essa opção não terá nenhum parâmetro.**  
  
 Parâmetros não podem ser definidos para essa opção. Somente o nome do comutador é necessário e não deve ser seguido por um vírgula.  
  
### Para corrigir este erro  
  
-   Digite o comando sem parâmetros para essa opção, isto é, em vez de digitar `msbuild /<switch>:<parameters>`, digite `msbuild /<switch>`  
  
-   Remova os dois\-pontos depois do nome do comutador, isto é, em vez de digitar `msbuild /<switch>:`, digite `msbuild /<switch>`  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)