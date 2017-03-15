---
title: "Erro MSB3181 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3181 (MSBuild)
**MSB3181: Dois ou mais arquivos têm o mesmo caminho de destino '\< caminho \>'.**  
  
 Esse aviso é gerado durante a geração de manifesto do aplicativo quando dois ou mais assemblies referenciados ou arquivos de compartilham o mesmo caminho de destino. O caminho inclui o nome do arquivo e todos esses assemblies substituirão uns aos outros no momento da implantação.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)