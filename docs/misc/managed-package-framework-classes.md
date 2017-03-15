---
title: "Pacote do Framework Classes gerenciadas | Microsoft Docs"
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
  - "estrutura de pacote gerenciado, classes auxiliares"
  - "classes do auxiliar de pacote gerenciado"
  - "O SDK do Visual Studio, gerenciados classes auxiliares de pacote"
  - "estrutura de pacote de classes [Visual Studio SDK] gerenciadas"
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Pacote do Framework Classes gerenciadas
Classes do framework \(MPF\) pacote gerenciado podem ser usadas para criar os VSPackages usando código gerenciado. Eles fornecem implementações padrão para várias interfaces de VSPackage. Ocultando as complexidades e detalhes de implementação MPF permite que você crie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] produtos de integração com uma quantidade mínima de código.  
  
> [!WARNING]
>  A maioria dos assemblies que contêm classes de estrutura de pacote gerenciado é fornecida com o SDK do Visual Studio. Você pode baixar o código\-fonte para a estrutura de pacotes gerenciados para projetos em [estrutura de pacote gerenciado para projetos](http://mpfproj11.codeplex.com/).  
  
## Namespaces MPF  
 A tabela a seguir lista os namespaces MPF fornecidos pelo [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
|Espaço para nome|Conteúdo|  
|----------------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contém classes úteis para tratamento de erros COM, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] constantes e windows Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Inclui os wrappers de código gerenciado para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projetos, editores e MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Inclui classes base MPF dos quais você pode derivar uma implementação de muitos objetos comuns do Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões do designer.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões do designer de serialização.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões do designer de CodeDom.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Oferece suporte ao projeto subtipos \(também conhecido como "tipos"\).|  
  
## Consulte também  
 [Os VSPackages e a estrutura de pacote gerenciado](/visual-cpp/misc/vspackages-and-the-managed-package-framework)   
 [Usando Assemblies de interoperabilidade do Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Os VSPackages e a estrutura de pacote gerenciado](/visual-cpp/misc/vspackages-and-the-managed-package-framework)