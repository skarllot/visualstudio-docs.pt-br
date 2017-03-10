---
title: "Erro MSB4136 (MSBuild) | Microsoft Docs"
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
  - "MSB4136"
ms.assetid: 6f0543d3-f8c0-44e1-8748-8a71be599bf4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB4136 (MSBuild)
**MSB4136: Erro ao ler informações de configuração.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] recebeu um erro quando tentou ler informações do conjunto de ferramentas para o arquivo de configuração de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] \(msbuild.exe.config\).  
  
### Para corrigir este erro  
  
-   Certifique\-se de que o arquivo de configuração é correto e bem formado.  Por exemplo, se você personalizou o arquivo .config adicionando um conjunto de ferramentas, verifique a definição do kit de ferramentas.  
  
## Consulte também  
 [Substituindo as configurações de ToolsVersion](../msbuild/overriding-toolsversion-settings.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)