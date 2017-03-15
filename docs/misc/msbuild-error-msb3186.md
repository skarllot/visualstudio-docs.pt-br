---
title: "Erro MSB3186 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoIdentity"
helpviewer_keywords: 
  - "MSB3186"
ms.assetid: 1219fef4-9114-401c-875b-1dc69697fd9f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3186 (MSBuild)
**MSB3186: Não é possível inferir identidade do assembly para o manifesto gerado a partir de parâmetros de entrada da tarefa.**  
  
 Esse erro é gerado quando o processo de compilação não é possível inferir um nome de assembly para o manifesto de implantação ou de aplicativo. O nome do assembly não é fornecido explicitamente. Não há nenhuma identidade no manifesto de base e a identidade do ponto de entrada não é especificado.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)