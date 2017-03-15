---
title: "Erro MSB4141 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB4141 (MSBuild)
**MSB4141: MSBuildToolsPath não é especificado para o ToolsVersion “\<x.x\>”.**  
  
 Um conjunto de ferramentas personalizado é definido mas nenhum valor é especificado para `MSBuildToolsPath`.  
  
### Para corrigir este erro  
  
-   Especificar um valor válido para `MSBuildToolsPath` quando você define um conjunto de ferramentas personalizado no Registro ou no arquivo de configuração de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .  
  
## Consulte também  
 [Configurações padrão e personalizadas do Toolset](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)