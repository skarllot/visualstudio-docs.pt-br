---
title: "Verificando subtipos de um projeto em tempo de execução | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 11
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
ms.openlocfilehash: 8a279543c5fc7b75244ae905c407df7a2ec3d025
ms.lasthandoff: 02/22/2017

---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Verificando subtipos de um projeto em tempo de execução
Um VSPackage depende de um subtipo de projeto personalizado deve incluir a lógica para procurar para que ele possa fazer normalmente se não houver o subtipo de subtipo. O procedimento a seguir mostra como verificar a presença de um subtipo especificado.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Para verificar a presença de um subtipo de  
  
1.  Obter a hierarquia de projeto dos objetos de projeto e a solução como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto adicionando o seguinte código para o VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Converter a hierarquia para o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>interface.</xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected>  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obter a lista de GUIDs de tipo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.</xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Verifique a lista para o GUID do subtipo especificado.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Subtipos de projeto](../extensibility/internals/project-subtypes.md)   
 [Design de subtipos de projeto](../extensibility/internals/project-subtypes-design.md)   
 [Propriedades e métodos estendidos por subtipos de projeto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
