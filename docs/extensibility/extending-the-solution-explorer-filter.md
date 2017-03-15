---
title: Estendendo o filtro do Solution Explorer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
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
ms.openlocfilehash: b66d49bda2c3e621a5d3dc0bd749a760e09d77f0
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-solution-explorer-filter"></a>Estendendo o filtro do Solution Explorer
Você pode estender **Solution Explorer** funcionalidade de filtro para mostrar ou ocultar arquivos diferentes. Por exemplo, você pode criar um filtro que mostre somente classe factory arquivos c# no **Solution Explorer**, como demonstra este passo a passo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Criar um projeto de pacote do Visual Studio  
  
1.  Crie um projeto do VSIX chamado `FileFilter`. Adicionar um modelo de item de comando personalizada chamado **FileFilter**. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Adicione uma referência ao `System.ComponentModel.Composition` e `Microsoft.VisualStudio.Utilities`.  
  
3.  Exibir o comando de menu no **Solution Explorer** barra de ferramentas. Abra o arquivo FileFilterPackage.vsct.  
  
4.  Alterar o `<Button>` bloco para o seguinte:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Atualizar o arquivo de manifesto  
  
1.  No arquivo source.extension.vsixmanifest, adicione um ativo que é um componente MEF.  
  
2.  Sobre o **ativos** guia, escolha o **novo** botão.  
  
3.  No **tipo** campo, escolha **Microsoft.VisualStudio.MefComponent**.  
  
4.  No **fonte** campo, escolha **um projeto na solução atual**.  
  
5.  No **projeto** campo, escolha **FileFilter**e, em seguida, escolha o **Okey** botão.  
  
### <a name="add-the-filter-code"></a>Adicione o código do filtro  
  
1.  Adicione alguns GUIDs para o arquivo FileFilterPackageGuids.cs:  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Adicione um arquivo de classe ao projeto FileFilter chamado FileNameFilter.cs.  
  
3.  Substitua o namespace vazio e a classe vazia com o código a seguir.  
  
     O `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` método utiliza a coleção que contém a raiz da solução (`rootItems`) e retorna a coleção de itens a serem incluídos no filtro.  
  
     O `ShouldIncludeInFilter` método filtra os itens do **Solution Explorer** hierarquia com base na condição de que você especificar.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  No FileFilter.cs, remova o código de tratamento e o posicionamento de comando do construtor FileFilter. O resultado deve ter esta aparência:  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Remova o método ShowMessageBox() também.  
  
5.  Em FileFilterPackage, cs, substitua o código no método Initialize () com o seguinte:  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Teste seu código  
  
1.  Compile e execute o projeto. Uma segunda instância do Visual Studio é exibida. Isso é chamado de instância experimental.  
  
2.  Na instância experimental do Visual Studio, abra um projeto c#.  
  
3.  Procure o botão que você adicionou na barra de ferramentas do Gerenciador de soluções. Ele deve ser o quarto botão da esquerda.  
  
4.  Quando você clica no botão, todos os arquivos devem ser filtrados e você deverá ver "todos os itens foram filtrados da exibição." no Solution Explorer.
