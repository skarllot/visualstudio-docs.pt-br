---
title: "Erro MSB2008 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB2008 (MSBuild)
**O sistema de projetos do Visual Studio não pode converter projetos "{0}". Ele só pode ser usado para converter projetos c\# e VB cliente.**  
  
 Válido somente [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projetos podem ser convertidos usando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Para corrigir este erro  
  
-   Se o projeto é um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] de projeto, verifique se o arquivo de projeto foi modificado ou corrompido. Se ele foi modificado ou corrompido, abra o projeto na versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em que ela foi criada, salvá\-lo e, em seguida, tentar convertê\-lo novamente.  
  
-   Se o projeto não é um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] do projeto, use a ferramenta apropriada para convertê\-lo.  
  
## Consulte também  
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)