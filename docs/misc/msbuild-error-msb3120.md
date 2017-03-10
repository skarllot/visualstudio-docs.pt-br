---
title: "Erro MSB3120 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3120 (MSBuild)
**MSB3120: A extensão de associação de arquivo '\< extensão \>' excede o comprimento máximo de \< maximumlength \>.**  
  
 O número de caracteres na extensão de associação de arquivo não deve exceder o número indicado.  
  
### Para corrigir este erro  
  
-   Definir o [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)`extension` de atributo para um valor que não tem mais caracteres do que o limite permitido para o sistema operacional de destino.  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)