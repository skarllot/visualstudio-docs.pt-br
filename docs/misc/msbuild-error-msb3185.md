---
title: "Erro MSB3185 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3185 (MSBuild)
**MSB3185: EntryPoint não especificado para manifesto.**  
  
 Esse erro é gerado quando um manifesto não especificar um ponto de entrada. Esse erro pode aplicar o manifesto do aplicativo e o manifesto de implantação.  
  
### Para corrigir este erro  
  
-   Se usando a tarefa GenerateApplicationManifest, verifique se você especifica um ponto de entrada válida ou defina a propriedade TargetFrameworkVersion para "v 3.5" ou superior. Para um manifesto do aplicativo, um ponto de entrada válido é um arquivo de .exe.  
  
-   Se usar a tarefa GenerateDeploymentManifest, certifique\-se de que você especifique os pontos de entrada válida em seus manifestos. Para um manifesto de implantação, um ponto de entrada válida é um manifesto de aplicativo.  
  
## Consulte também  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)   
 [Erro MSB3116 \(MSBuild\)](../misc/msbuild-error-msb3116.md)   
 [Erro MSB3117 \(MSBuild\)](/visual-cpp/misc/msbuild-error-msb3117)   
 [Erro MSB3118 \(MSBuild\)](../misc/msbuild-error-msb3118.md)   
 [Erro MSB3174 \(MSBuild\)](/visual-cpp/misc/msbuild-error-msb3174)