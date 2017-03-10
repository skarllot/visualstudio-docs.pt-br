---
title: "Perguntas freq&#252;entes sobre instala&#231;&#227;o e implanta&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "implantação [SDK do Visual Studio]"
  - "LCID [SDK do Visual Studio]"
  - "instalação [SDK do Visual Studio]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Perguntas freq&#252;entes sobre instala&#231;&#227;o e implanta&#231;&#227;o
Este tópico aborda questões da [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] a comunidade de usuários sobre a instalação e implantação.  O tópico continuará a ser atualizado com novo conteúdo da comunidade.  
  
## Contents  
  
-   [Determinando o LCID de uma instalação de Visual Studio programaticamente](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> Determinando o LCID de uma instalação de Visual Studio programaticamente  
 **P:**  há uma maneira para determinar programaticamente o LCID de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalação?  
  
 **R:** <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>retornará o LCID da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em uso no momento.  
  
## Consulte também  
 [Liberar um produto](../misc/releasing-a-visual-studio-integration-product.md)