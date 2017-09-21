---
title: Gerenciamento de projetos do Windows Universal | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 14
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
ms.openlocfilehash: f99c7369c426c5f51aa795af912d0d8594b0e248
ms.lasthandoff: 02/22/2017

---
# <a name="managing-universal-windows-projects"></a>Gerenciamento de projetos do Windows Universal
Aplicativos universais do Windows são aplicativos voltados para Windows 8.1 e Windows Phone 8.1, permitindo que os desenvolvedores usem o código e outros ativos em ambas as plataformas. O código compartilhado e recursos são mantidos em um projeto compartilhado, enquanto o código específico da plataforma e recursos são mantidos em projetos separados, um para o Windows e outro para Windows Phone. Para obter mais informações sobre aplicativos Windows universais, consulte [aplicativos universais do Windows](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Extensões do Visual Studio que gerenciar projetos devem estar cientes de que os projetos de aplicativo universais do Windows têm uma estrutura diferente dos aplicativos de plataforma única. Este passo a passo mostra como navegar projeto compartilhado e gerenciar os itens compartilhados.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Navegue projeto compartilhado  
  
1.  Crie um projeto do VSIX c# chamado **TestUniversalProject**. (**, Novo, projeto** e **o pacote do Visual Studio c#, extensibilidade,**). Adicionar uma **comando personalizado** modelo de item de projeto (no Gerenciador de soluções, clique com botão direito no nó do projeto e selecione **Adicionar / Novo Item**, em seguida, vá para **extensibilidade**). Nomeie o arquivo **TestUniversalProject**.  
  
2.  Adicione uma referência ao Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll e Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (no **extensões** seção).  
  
3.  Abra TestUniversalProject.cs e adicione o seguinte `using` instruções:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  Na classe TestUniversalProject, adicione um campo particular apontando para o **saída** janela.  
  
    ```c#  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Defina a referência ao painel Saída dentro do construtor de TestUniversalProject:  
  
    ```c#  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  
  
6.  Remova o código existente do `ShowMessageBox` método:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Obtenha o objeto DTE, que usaremos para várias finalidades diferentes neste passo a passo. Além disso, certifique-se de que uma solução é carregada quando o botão de menu é clicado.  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  
  
8.  Localize o projeto compartilhado. O projeto compartilhado é um contêiner puro; não criar ou produzir saídas. O método a seguir localiza o primeiro projeto compartilhado na solução, procurando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto que tem a capacidade de projeto compartilhado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    ```c#  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  
  
        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  
  
9. No `ShowMessageBox` método, a legenda de saída (o nome do projeto que aparece no **Solution Explorer**) de projeto compartilhado.  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  
  
10. Obtenha o projeto de plataforma ativa. Projetos da plataforma são os projetos que contêm recursos e código específico da plataforma. O método a seguir usa o novo campo <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>para manter o projeto de plataforma ativa.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>  
  
    ```c#  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  
  
11. No `ShowMessageBox` método, a legenda do projeto plataforma ativa de saída.  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  
  
                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  
  
    ```  
  
12. Itere através dos projetos de plataforma. O método a seguir obtém todos os projetos (plataforma) importação de projeto compartilhado.  
  
    ```c#  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  Se o usuário abrir um projeto de aplicativo do Windows universal C++ na instância experimental, o código acima gera uma exceção. Este é um problema conhecido. Para evitar a exceção, substitua o `foreach` bloco acima com o seguinte:  
  
    ```c#  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. No `ShowMessageBox` método, a legenda de cada projeto da plataforma de saída. Insira o seguinte código após a linha que gera a legenda do projeto plataforma ativa. Somente os projetos de plataforma são carregados aparecem nessa lista.  
  
    ```c#  
    output.OutputStringThreadSafe("Platform projects:\n");  
  
    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  
  
    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  
  
14. Altere o projeto de plataforma ativa. O método a seguir define o projeto ativo usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>  
  
    ```c#  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. No `ShowMessageBox` método, altere o projeto de plataforma ativa. Inserir esse código dentro de `foreach` bloco.  
  
    ```c#  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
  
        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  
  
16. Agora experimente. Pressione F5 para iniciar a instância experimental. Criar um projeto de aplicativo de hub universal c# na instância experimental (no **novo projeto** caixa de diálogo, **Visual c# / Windows / Windows 8 / Universal / App Hub**). Depois que a solução é carregada, vá para o **ferramentas** menu e clique em **invocar TestUniversalProject**e, em seguida, verifique o texto **saída** painel. Você verá algo semelhante ao seguinte:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Gerenciar os itens compartilhados no projeto de plataforma  
  
1.  Localize os itens compartilhados no projeto de plataforma. Os itens no projeto compartilhado aparecem no projeto de plataforma como itens compartilhados. Você não pode vê-los no **Solution Explorer**, mas você pode ir a hierarquia de projeto para encontrá-los. O método a seguir percorre a hierarquia e coleta todos os itens compartilhados. Opcionalmente, ele produz a legenda de cada item. Os itens compartilhados são identificados pela nova propriedade <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>  
  
    ```c#  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  
  
        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  
  
        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
  
            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  
  
2.  No `ShowMessageBox` método, adicione o seguinte código para percorrer os itens de hierarquia de projeto de plataforma. Inseri-lo dentro do `foreach` bloco.  
  
    ```c#  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Ler os itens compartilhados. Os itens compartilhados aparecem no projeto de plataforma como ocultados arquivos vinculados, e você pode ler todas as propriedades como arquivos vinculados comuns. O código a seguir lê o caminho completo do primeiro item compartilhado.  
  
    ```c#  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Agora experimente. Pressione F5 para iniciar a instância experimental. Criar um projeto de aplicativo de hub universal c# na instância experimental (no **novo projeto** caixa de diálogo, **Visual c# / Windows / Windows 8 / Universal / App Hub**) para o **ferramentas** menu e clique em **invocar TestUniversalProject**e, em seguida, verifique o texto **saída** painel. Você verá algo semelhante ao seguinte:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Detectando alterações em projetos compartilhados e plataforma  
  
1.  Você pode usar eventos de hierarquia e de projeto para detectar alterações em projetos compartilhados, exatamente como faria para projetos da plataforma. No entanto, os itens de projeto no projeto compartilhado não são visíveis, o que significa que certos eventos não são acionados quando itens de projeto compartilhado são alterados.  
  
     Considere a sequência de eventos quando um arquivo em um projeto é renomeado:  
  
    1.  O nome do arquivo é alterado no disco.  
  
    2.  O arquivo de projeto é atualizado para incluir o novo nome do arquivo.  
  
     Eventos de hierarquia (por exemplo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) geralmente acompanhar as alterações exibidas na interface do usuário, como de **Solution Explorer**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> Eventos de hierarquia considere uma operação de renomeação de arquivo para consistem de exclusão de um arquivo e, em seguida, a adição de um arquivo. No entanto, quando invisíveis itens forem alterados, o sistema de eventos de hierarquia aciona um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>eventos, mas não um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>evento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> Portanto, se você renomear um arquivo em um projeto de plataforma, você obter ambos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, mas se você renomear um arquivo em um projeto compartilhado, você obtém apenas <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>  
  
     Para controlar as alterações em itens de projeto, você pode manipular eventos de item de projeto do DTE (aqueles encontrados no <xref:EnvDTE.ProjectItemsEventsClass>).</xref:EnvDTE.ProjectItemsEventsClass> No entanto, se você lidar com grandes números de eventos, você pode obter um desempenho melhor manipulação de eventos no <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Neste passo a passo, vamos mostrar apenas os eventos de hierarquia e os eventos DTE. Neste procedimento você adicionar um ouvinte de eventos para um projeto compartilhado e um projeto de plataforma. Em seguida, quando você renomeia um arquivo em um projeto compartilhado e outro em um projeto de plataforma, você pode ver os eventos que são acionados para cada operação de renomeação.  
  
     Neste procedimento você adicionar um ouvinte de eventos para um projeto compartilhado e um projeto de plataforma. Em seguida, quando você renomeia um arquivo em um projeto compartilhado e outro em um projeto de plataforma, você pode ver os eventos que são acionados para cada operação de renomeação.  
  
2.  Adicione um ouvinte de eventos. Adicione um novo arquivo de classe ao projeto e chame-HierarchyEventListener.cs.  
  
3.  Abra o arquivo HierarchyEventListener.cs e adicione as seguintes instruções using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  Ter o `HierarchyEventListener` classe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Implemente os membros das <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, como no código a seguir.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    {  
        private IVsHierarchy hierarchy;  
        IVsOutputWindowPane output;   
  
        internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
             this.hierarchy = hierarchy;  
             this.output = outputWindow;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
    }  
  
    ```  
  
6.  Na mesma classe adicionar outro manipulador de eventos para o evento DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, que ocorre sempre que um item de projeto é renomeado.</xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>  
  
    ```c#  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Inscreva-se para os eventos de hierarquia. Você precisa inscrever separadamente para cada projeto que você estiver rastreando. Adicione o seguinte código no `ShowMessageBox`, um para o projeto compartilhado e outro para um dos projetos de plataforma.  
  
    ```c#  
    // hook up the event listener for hierarchy events on the shared project  
    HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
    uint cookie1;  
    sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  
  
    // hook up the event listener for hierarchy events on the   
    active project  
    HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
    uint cookie2;  
    activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
    ```  
  
8.  Inscreva-se para o evento de item de projeto DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>.</xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> Adicione o seguinte código depois de você conecta o segundo ouvinte.  
  
    ```c#  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Modifica o item compartilhado. Você não pode modificar itens compartilhados em um projeto de plataforma; em vez disso, você deve modificá-las no projeto compartilhado que é o proprietário real desses itens. Você pode obter a ID do item correspondente no projeto compartilhado, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>dando a ele caminho completo do item compartilhado</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> Em seguida, você pode modificar o item compartilhado. A alteração é propagada para os projetos de plataforma.  
  
    > [!IMPORTANT]
    >  Você deve saber se um item de projeto é um item compartilhado antes de modificá-lo.  
  
     O método a seguir modifica o nome de um arquivo de item de projeto.  
  
    ```c#  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  
  
10. Chamar esse método após todos os outros códigos no `ShowMessageBox` para modificar o nome do arquivo do item no projeto compartilhado. Insira este após o código que obtém o caminho completo do item no projeto compartilhado.  
  
    ```c#  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Compile e execute o projeto. Criar um aplicativo de hub universal c# na instância experimental, vá para o **ferramentas** menu e clique em **TestUniversalProject invocar**e o texto no painel de saída geral. O nome do primeiro item compartilhado (Esperamos que ele seja o arquivo App. XAML) do projeto deve ser alterado e você verá que o <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>evento foi disparado.</xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> Nesse caso, como renomear o XAML faz com que o App.xaml.cs a ser renomeado, bem, você deve ver quatro eventos (dois para cada projeto de plataforma). (Eventos DTE não rastrear os itens no projeto compartilhado.) Você deverá ver duas <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>eventos (um para cada um dos projetos da plataforma), mas nenhum <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>eventos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>  
  
12. Agora, tente renomear um arquivo em um projeto de plataforma, e você pode ver a diferença nos eventos acionada. Adicione o seguinte código no `ShowMessageBox` após a chamada para `ModifyFileName`.  
  
    ```c#  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. Compile e execute o projeto. Criar um projeto Universal c# na instância experimental, vá para o **ferramentas** menu e clique em **TestUniversalProject invocar**e o texto no painel de saída geral. Depois que o arquivo do projeto de plataforma é renomeado, você deve ver ambos um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>eventos e um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>evento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> Uma vez que o arquivo não causou nenhum outro arquivo a ser alterado e, como alterações nos itens de um projeto de plataforma não são propagadas em qualquer lugar, há apenas um desses eventos.
