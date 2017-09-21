---
title: Mantendo a propriedade de um Item de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
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
ms.openlocfilehash: 2edc6e8d6ddc1001dd2859b121ede3b8703118d7
ms.lasthandoff: 02/22/2017

---
# <a name="persisting-the-property-of-a-project-item"></a>Mantendo a propriedade de um Item de projeto
Você talvez queira manter uma propriedade que você adicionar a um item de projeto, como o autor de um arquivo de origem. Você pode fazer isso com o armazenamento de propriedade no arquivo de projeto.  
  
 A primeira etapa para manter uma propriedade em um arquivo de projeto é obter a hierarquia do projeto como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Você pode obter essa interface usando automação ou usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> Depois de obter a interface, você pode usá-lo para determinar qual item de projeto está selecionado no momento. Uma vez que a ID do item de projeto, você pode usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>para adicionar a propriedade.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>  
  
 Nos procedimentos a seguir, você manter a propriedade de VsPkg.cs `Author` com o valor `Tom` no arquivo de projeto.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Para obter a hierarquia de projeto com o objeto DTE  
  
1.  Adicione o seguinte código para o VSPackage:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Para manter a propriedade de item de projeto com o objeto DTE  
  
1.  Adicione o seguinte código para o código fornecido no método no procedimento anterior:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Para obter a hierarquia de projeto usando IVsMonitorSelection  
  
1.  Adicione o seguinte código para o VSPackage:  
  
    ```c#  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2.  
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Para manter a propriedade de item de projeto selecionado, dada a hierarquia de projeto  
  
1.  Adicione o seguinte código para o código fornecido no método no procedimento anterior:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Para verificar se a propriedade é persistida  
  
1.  Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e, em seguida, abra ou crie uma solução.  
  
2.  Selecione o projeto item VsPkg.cs na **Solution Explorer**.  
  
3.  Use um ponto de interrupção ou caso contrário, determinar que o VSPackage é carregado e SetItemAttribute é executado.  
  
    > [!NOTE]
    >  Você pode carregar um VSPackage automaticamente no contexto da interface do usuário <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>.</xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists> Para obter mais informações, consulte [VSPackages Carregando](../extensibility/loading-vspackages.md).  
  
4.  Fechar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e, em seguida, abra o arquivo de projeto no bloco de notas. Você deve ver o \<autor > marca com o valor de Tom, da seguinte maneira:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas personalizadas](../extensibility/internals/custom-tools.md)
