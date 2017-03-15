---
title: "Carga de solução leve (LSL) | Documentos do Microsoft"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
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
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>Carga de solução leve (LSL)

## <a name="background-information-on-lsl"></a>Informações gerais sobre LSL

Solução leve de carga é um novo recurso em 2017 VS que reduzirá significativamente o tempo de carregamento de solução, permitindo que você seja mais produtivo rapidamente. Quando LSL está habilitado, Visual Studio não será totalmente carregado projetos até começar a trabalhar com eles.

LSL pode afetar extensões do Visual Studio. Extensões cujos recursos dependem de um projeto a ser carregado podem não funcionar ou funcionem corretamente sem seguir as diretrizes detalhadas neste documento.

Para obter mais informações sobre LSL, use os links a seguir:

* [Blog de carga de solução leve](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Dúvidas? Entre em contato conosco em[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Habilitar a configuração para carregar projetos no modo "adiado"

1. Feche qualquer solução atualmente aberta.
2. Vá para **ferramentas** > **opção** > **projetos e soluções** > **geral** página de configurações.
3. Verifique o **carga de solução leve** caixa para habilitar a configuração.

Quando uma solução é aberta com a configuração acima ativada, o IDE mostra um modo de exibição normal dos projetos, mas os projetos não são carregados.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Diferenças entre carregamento diferido e carga regular de projetos

Com a carga de solução leve, projetos não são carregados quando abrir uma solução. Esses "projetos adiada," uma hierarquia de stub é criada. O Gerenciador de soluções mostra a exibição esperada com ícones e nomes de projetos, não há nenhuma indicação de interface do usuário que alguns ou todos os projetos estão em "modo adiado".

Com LSL habilitado, extensões não podem esperar que os projetos necessários já totalmente sejam carregados quando uma operação é disparada. Os chamadores precisam verificar se eles têm uma dependência em projetos carregados. Se uma extensão requer informações de um projeto adiada, a extensão faça o seguinte:

1. Carregar os projetos conforme necessário.
2. Use o novo **APIs do espaço de trabalho** para obter informações de um projeto adiado sem carregá-lo.

O novo **APIs do espaço de trabalho** Permitir extensões obter informações, como o projeto de um arquivo de origem e todos os arquivos de origem para um projeto específico, de um projeto adiado. Em alguns casos, apenas um conjunto limitado de projetos precisa ser carregado. A opção certa é um equilíbrio entre a frequência das operações, facilidade de abordagens alternativas e a experiência geral do usuário.

Todos os projetos e carga de solução relacionados a eventos são disparados ainda no modo LSL. Isso permite que componentes obter o comportamento esperado do VS e se comportam da mesma maneira como quando os projetos são carregados. O carregamento do projeto relacionados ao trabalho realizado durante a solução aberta é drasticamente reduzido embora.

## <a name="ui-requirements-and-changes"></a>Requisitos de interface do usuário e alterações

Toda interface do usuário deve tratar carregados e adiados projetos como iguais. Isso significa que todas as ações que podem ser executadas em um projeto carregado devem ser aplica a projetos adiados, com algumas exceções. Para ajudar a recursos de fazer isso, há alterações algumas APIs de plataforma existentes, bem como a introdução de novas APIs.

### <a name="expectations-for-ui"></a>Expectativas para a interface do usuário

1. Recursos devem mostrar que nenhum visual diferenças dependendo se projetos forem carregados ou adiados.
2. Qualquer listagem ou enumeração sobre os projetos da solução carregada deve incluir projetos adiados.
3. Qualquer ação disponível em um projeto carregado deve estar disponível em um projeto adiado.
4. Recursos deve projetos de solicitação para carregar somente quando:
  * Não há interação direta do usuário com um recurso. Não carregar preventivamente projetos.
  * Um gesto "Ver mais resultados" é feito pelo usuário. Veja abaixo dessa diretriz de interface do usuário.
  * Somente o projeto totalmente carregado pode ser usado para satisfazer a ação. Usar LSL e APIs abertas do projeto sempre que possível e enviar a solicitação de recurso pede quando a funcionalidade está ausente.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Alterações na plataforma de APIs para ajudar a levar a interface do usuário

1. Novas APIs são fornecidas para perguntar a solução se ele foi aberto no modo de carregamento da solução leve e quantos projetos estão em um estado adiado.
2. Novo evento é fornecido para quando todos os projetos adiados são carregados na solução.
3. Novas APIs são fornecidas para solicitar um projeto se ele é adiado.
4. APIs existentes são atualizados para incluir projetos adiados quando se pede para projetos carregados.
5. APIs existentes são atualizados para express a solução é totalmente carregado após a solução for aberta.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Como adicionar "Ver mais resultados" para um recurso.

Considere o impacto dos projetos adiados recursos que executam uma consulta no conteúdo de projetos. Em algumas situações, recursos podem obter os resultados de sua consulta de LSL e APIs do espaço de trabalho para um projeto adiado. Em outros casos, limitações do recurso exigem projetos a serem carregados. Ambas as situações devem fornecer um novo gesto "Ver mais resultados" que permite aos usuários carregar totalmente projetos e consultar novamente. Esse gesto habilita recursos fornecer uma melhor aproximação quando há projetos adiados ao dar ao usuário uma maneira de obter o resultado perfeito quando projetos são de fato carregados.

O algoritmo geral de recursos deve ser:

### <a name="when-the-query-is-performed-over-a-single-project"></a>Quando a consulta é executada em um único projeto

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Quando a consulta é executada ao longo de toda a solução

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>Alterações na API

### <a name="new-api"></a>Nova API

IVsSolution7.IsSolutionLoadDeferred (out bool adiada)

Retornará true se a solução atual foi carregada no modo adiado. Observe que se a solução inicialmente foi carregada no modo adiado, mesmo se todos os projetos adiados, eventualmente, são carregados na sessão atual (devido à gestos do usuário explícito ou forçado por operações), essa propriedade ainda retornará true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Retorna a contagem de projetos atualmente no modo adiado. Esta propriedade terá um valor no intervalo [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Retorna VERDADEIRO se uma hierarquia de projeto estiver no estado de carregamento adiada.

__VSENUMPROJFLAGS3 com valores EPF_DEFERRED e EPF_NOTDEFERRED

Esses sinalizadores podem ser passados para [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) para iterar sobre projetos adiados e não adiada.

### <a name="new-events"></a>Novos eventos

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Esse evento é gerado depois que todos os projetos adiados foram carregados. Neste ponto, VSPROPID_DeferredProjectCount é igual a 0. Observe que este evento não é gerado como parte da carga de solução e não pode ser gerado de uma sessão. Ele só é acionado quando todos os projetos adiados são carregados.

### <a name="changes-to-existing-api"></a>Alterações para a API existente

* Passando [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION para [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) retorna adiada projetos.
* Passando [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION não retorna projetos adiados.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) é definido como true na solução aberta. Projetos adiados são tratados como carregados para esse contexto é definido muito anterior no modo de não-LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount retorna a soma dos projetos carregados e adiadas.

## <a name="helpful-code-snippets"></a>Trechos de código útil

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Verifique se uma solução foi aberta no modo de carregamento diferido

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Verifique se um projeto é adiado

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Carregar um projeto

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Carregar um conjunto de projetos

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Verifica se a solução foi adiada projetos

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Obtendo informações detalhadas com APIs do espaço de trabalho

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Como obter informações detalhadas sobre uma solução LSL

Novas APIs de espaço de trabalho são expostos por meio de IVsSolutionWorkspaceService para ajudar a recuperar informações detalhadas sobre uma solução.

Essas APIs podem ser usadas para obter o espaço de trabalho atual, a solução ativa, as informações de linha de comando gerenciado, bem como o serviço de índice do espaço de trabalho. Essas APIs podem aproveitar ainda mais o serviço de índice para obter dados detalhados, por exemplo, todos os arquivos de origem em um projeto, o projeto de um arquivo de origem, todos os projetos contidos na solução atual, todas as referências de P2P em um projeto, etc.

Os trechos de código a seguir demonstram o uso das APIs do espaço de trabalho.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Obter IVsSolutionWorkspaceService inicialmente

>**Observação:** Obtenha apenas IVsSolutionWorkspaceService em cenários LSL para evitar o carregamento do pacote de API do espaço de trabalho.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Observação:** os trechos a seguir pressupõem _solutionWorkspaceService lentamente já foi inicializado.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Obter informações de linha de comando gerenciado adiados projetos para a configuração de solução ativa

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Obtenha o arquivo de solução ativa no LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Obtenha o projeto do proprietário de um arquivo de origem

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Obter todos os arquivos de origem de um projeto

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Obter referências a P2P em um projeto

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Obter todos os projetos em uma solução

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Solução de problemas

Devido à natureza de LSL, é intencional de que os usuários não possam ver a diferença entre projetos carregados e adiadas. Isso pode dificultar recursos de desenvolvimento e teste.

Você pode habilitar dicas visuais na interface do usuário para projetos adiados, fazendo o seguinte:

1. Feche o Visual Studio
2. Regedit.exe
3. Selecione HKLM
4. Arquivo > Carregar Hive
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Digite "VisualStudio" como um nome de chave
7. Definir `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Selecione HKLM\VisualStudio
9. Arquivo > Descarregar Hive
10. Inicie o Visual Studio

Para mais dúvidas, entre em contato [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).







