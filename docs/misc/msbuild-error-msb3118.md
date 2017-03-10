---
title: "Erro MSB3118 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3118 (MSBuild)
**Msb3118 \(\): O aplicativo está configurado para usar a confiança do aplicativo, mas TargetFrameworkVersion não for v 3.5.**  
  
 Esse erro ocorre quando você definir o <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> propriedade `True` e defina o <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> propriedade para uma versão inferior a `v3.5` \(por exemplo, `v2.0`\).  
  
### Para corrigir este erro  
  
-   Definir o <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> propriedade `v3.5` ou superior.  
  
## Consulte também  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Erro MSB3116 \(MSBuild\)](../misc/msbuild-error-msb3116.md)   
 [Erro MSB3117 \(MSBuild\)](/visual-cpp/misc/msbuild-error-msb3117)   
 [Erro MSB3119 \(MSBuild\)](../misc/msbuild-error-msb3119.md)   
 [Erro MSB3174 \(MSBuild\)](/visual-cpp/misc/msbuild-error-msb3174)   
 [Erro MSB3185 \(MSBuild\)](../misc/msbuild-error-msb3185.md)