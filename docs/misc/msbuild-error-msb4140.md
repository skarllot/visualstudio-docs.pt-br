---
title: "Erro MSB4140 (MSBuild) | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB4140 (MSBuild)
**MSB4140: ToolsVersion padrão é especificado ou no Registro ou no arquivo de configuração.**  
  
 O projeto não especificar um valor padrão de `ToolsVersion` .  Portanto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] não souber valor a ser usado.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que um valor de `DefaultToolsVersion` é especificado tanto no Registro onde os conjuntos de ferramentas são definidos, ou em um arquivo de configuração \(como msbuild.exe.config\).  
  
## Consulte também  
 [Configurações padrão e personalizadas do Toolset](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)