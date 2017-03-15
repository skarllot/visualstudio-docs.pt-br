---
title: "Erro MSB1016 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1016 (MSBuild)
**Especifique o nível de detalhamento.**  
  
 Um nível de detalhamento deve ser especificado para o **\/verbosity** alternar.  
  
### Para corrigir este erro  
  
1.  Especifique o nível de detalhamento usando o formato `/verbosity:<level>`. Os níveis de verbosidade disponíveis são: q \[uiet\], m \[IMO\], n \[ormal\], d \[etalhada\] e diag \[nostic\], por exemplo, `/verbosity:quiet`, `/verbosity:q`, ou `/v:q`  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)