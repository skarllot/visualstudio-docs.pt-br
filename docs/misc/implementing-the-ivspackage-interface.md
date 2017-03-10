---
title: "Implementando a Interface IVsPackage | Microsoft Docs"
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
  - "Interface IVsPackage"
  - "interfaces, Implementando IVsPackages"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Implementando a Interface IVsPackage
Todos os VSPackages deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]chama os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> para inicializar e VSPackages fechar, para obter páginas de propriedade associada e por outros motivos.  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface é a interface de gateway entre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e VSPackage.  
  
 Você pode escrever um VSPackage gerenciado como uma subclasse da <xref:Microsoft.VisualStudio.Shell.Package> , de classe que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> em seu nome.  Para obter mais informações, consulte [VSPackages gerenciados](../misc/managed-vspackages.md).  
  
> [!NOTE]
>  Muito do código não gerenciado de exemplo na seção Integração de Visual Studio a [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] usa a biblioteca de ATL \(Active Template\).  Você não precisará usar a ATL para criar os VSPackages, mas você deve compreender a ATL para entender o código de exemplo.  
  
## Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)