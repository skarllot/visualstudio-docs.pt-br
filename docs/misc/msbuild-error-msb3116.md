---
title: "Erro MSB3116 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3116 (MSBuild)
**MSB3116: O aplicativo está marcado como host no navegador, mas também está marcado para uso online e offline. Só altere seu aplicativo online.**  
  
 Ao implantar um aplicativo de navegador WPF Web, você deve definir o <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> propriedade `True`. Quando <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> é definido como `True`, você deve definir o <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> propriedade `False` \(para disponibilizar a instalação online somente\). Se a segunda condição não for atendida, você receberá essa mensagem de erro.  
  
### Para corrigir este erro  
  
-   Definir o <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> propriedade `False`.  
  
## Consulte também  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)