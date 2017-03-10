---
title: "Erro MSB3121 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationMissingAttribute"
helpviewer_keywords: 
  - "MSB3121"
ms.assetid: c1e83a2a-515f-412d-b8b7-4821e510a923
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3121 (MSBuild)
**MSB3121: O elemento de associação de arquivo no manifesto do aplicativo está faltando um ou mais dos seguintes atributos: extensão, descrição, progid ou ícone padrão.**  
  
 O [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) deve conter valores para todos os quatro atributos.  
  
### Para corrigir este erro  
  
-   Defina cada [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) de atributo para um valor válido.  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)