---
title: Estendendo o modelo de objeto do projeto Base | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6e1ef71e9a17c6e80efb6c3598a0578f88e2afbf
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-object-model-of-the-base-project"></a>Estendendo o modelo de objeto do projeto Base
Um subtipo de projeto pode estender o modelo de objeto de automação do projeto base nos seguintes locais:  
  
-   Project.Extender ("\<ProjectSubtypeName >") – isso permite que um subtipo de projeto oferece um objeto com métodos personalizados de <xref:EnvDTE.Project>.</xref:EnvDTE.Project> Um subtipo de projeto pode usar extensores de automação para expor o `Project` objeto. O <xref:EnvDTE80.IInternalExtenderProvider>interface implementada no agregador de subtipo de projeto principal deve oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>(correspondente a um `itemid` valor de VSITEMID_ROOT, de `VSITEMID`) CATID.</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >") – isso permite que um subtipo de projeto oferece um objeto com métodos personalizados de um determinado <xref:EnvDTE.ProjectItem>objeto dentro do projeto.</xref:EnvDTE.ProjectItem> Um subtipo de projeto pode usar extensores de automação para expor esse objeto. O <xref:EnvDTE80.IInternalExtenderProvider>interface implementada no agregador de subtipo de projeto principal precisa oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>(correspondente a um desejado `VSITEMID`) CATID.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   Properties – essa coleção expõe as propriedades de configuração independente do `Project` objeto. Para obter mais informações sobre propriedades de projeto, consulte <xref:EnvDTE.Project.Properties%2A>.</xref:EnvDTE.Project.Properties%2A> Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades para esta coleção. O <xref:EnvDTE80.IInternalExtenderProvider>interface implementada no agregador de subtipo de projeto principal precisa oferecer seu objeto para o `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondente a um `itemid` valor de VSITEMID_ROOT, de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   Configuration.Properties – esta coleção expõe as propriedades dependentes de configuração do projeto para uma configuração específica (por exemplo, Debug). Para obter mais informações, consulte <xref:EnvDTE.Configuration>.</xref:EnvDTE.Configuration> Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades para esta coleção. O <xref:EnvDTE80.IInternalExtenderProvider>interface implementada no agregador de subtipo de projeto principal oferece seu objeto para o CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondente a um `itemid` valor de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>).</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> </xref:EnvDTE80.IInternalExtenderProvider> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interface é usada para diferenciar um objeto de procura de configuração do outro.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID></xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
