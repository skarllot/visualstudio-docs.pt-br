---
title: "Servi&#231;os usados nos exemplos | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "serviços, que aparecem nos exemplos"
  - "exemplos de serviços"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Servi&#231;os usados nos exemplos
Os exemplos incluídos na [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fazer uso de muitos serviços.  A lista a seguir mostra que vários comumente usados serviços e as amostras de usá\-los.  
  
> [!NOTE]
>  Se a referência e amostras sem suporte estão disponíveis, apenas a amostra de referência está listada.  
  
|Serviço|Exemplo|  
|-------------|-------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEdit, ProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[Como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|Preterido.  Use <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> em vez disso.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|Exemplo de Reference.HelpIntegration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Exemplo de SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|Exemplo de SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.Package, Reference.ToolWindow e muitos outros exemplos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Exemplo de SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.Package, Reference.ToolWindow e muitos outros exemplos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdt, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditor, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindow, BscEdit e muitos outros exemplos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## Consulte também  
 [Lista de serviços disponíveis](../extensibility/internals/list-of-available-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)