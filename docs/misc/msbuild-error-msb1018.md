---
title: "Erro MSB1018 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.InvalidVerbosityError"
helpviewer_keywords: 
  - "MSB1018"
ms.assetid: fb4deacc-a799-44e8-8980-d70d9da4caa1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1018 (MSBuild)
**Nível de detalhamento não é válido.**  
  
 O detalhamento especificado não é um dos níveis de verbosidade disponíveis.  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia do nível de detalhamento. Os níveis de verbosidade disponíveis são: q \[uiet\], m \[IMO\], n \[ormal\], d \[etalhada\] e diag \[nostic\], por exemplo, `/verbosity:quiet`, `/verbosity:q`, ou `/v:q`  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)   
 [Agentes de log de compilação](../msbuild/build-loggers.md)