---
title: "Erro MSB1027 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1027 (MSBuild)
**A opção \/noautoresponse não pode ser especificada no arquivo de resposta automática MSBuild, nem em qualquer arquivo de resposta que é referenciado pelo arquivo de resposta automática.**  
  
 O **\/noautoresponse** switch foi encontrado no arquivo MSBuild, ou em outro arquivo de resposta incluídos pelo arquivo MSBuild. O arquivo de resposta automática não pode ser usado para desativar em si.  
  
### Para corrigir este erro  
  
-   Especifique um arquivo de resposta  
  
-   Remover o **\/noautoresponse** alternar do arquivo de resposta do MSBuild.  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)