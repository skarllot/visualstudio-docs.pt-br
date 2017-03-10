---
title: "Erro MSB3124 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3124 (MSBuild)
**MSB3124: Uma associação de arquivo já foi criada para a extensão '\< extensionname \>'.**  
  
 Esse erro ocorre quando uma extensão de associação de arquivo duplicado é encontrada.  
  
### Para corrigir este erro  
  
-   Remover [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)`extension` atributos que não são exclusivos. Atributos de extensão do elemento cada \< fileAssociation \> listados devem ser exclusivos.  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)