---
title: "Erro MSB4133 (MSBuild) | Microsoft Docs"
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
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB4133 (MSBuild)
**MSB4133: Uma versão das ferramentas padrão "\< x.x. \>" foi especificada, mas não foi possível localizar a sua definição.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] não é possível localizar o conjunto de ferramentas que é definido no arquivo de projeto como o `DefaultToolsVersion`.  
  
### Para corrigir este erro  
  
-   Verifique se `DefaultToolsVersion` está especificado corretamente, e que esse conjunto de ferramentas é definido no registro ou no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo de configuração.  
  
## Consulte também  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)