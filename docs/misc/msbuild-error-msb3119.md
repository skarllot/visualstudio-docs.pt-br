---
title: "Erro MSB3119 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3119 (MSBuild)
**MSB3119: As extensões de associações de arquivo devem começar com um caractere de ponto \(.\).**  
  
 Esse erro ocorre quando você configurar uma associação de arquivo e a extensão não começa com um caractere de ponto \(.\).  
  
### Para corrigir este erro  
  
-   Definir o [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)`extension` atributo para um valor que começa com um caractere de ponto \(.\), por exemplo, ". doc".  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)