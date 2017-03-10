---
title: "Estendendo o Gerenciador de refer&#234;ncias | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb43a2a0-be0f-4ef4-96e8-8fc940e9389e
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Estendendo o Gerenciador de refer&#234;ncias
Você pode adicionar referências ao seu projeto usando o Gerenciador de referência em uma extensão do Visual Studio. Antes do Gerenciador de referências é exibida, devem configurar seus projetos para mostrar os dados nos locais corretos. Por exemplo, um projeto que tem como alvo o [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] deve preencher os assemblies de uma pasta diferente de um projeto que tem como alvo o [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)].  
  
 Normalmente, você configurar o Gerenciador de referência usando uma coleção de ProviderContexts dos seguintes provedores:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsAssemblyReferenceProviderContext>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsComReferenceProviderContext>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileReferenceProviderContext>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectReferenceProviderContext>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPlatformReferenceProviderContext>  
  
 Um componente de cliente exibe o Gerenciador de referências, chamando o método ShowReferenceManager no serviço do Visual Studio chamado SVsReferenceManager. Uma coleção de classes IVsReferenceProviderContext é passada para esse método como um argumento. Nesses contextos determinam quais guias aparecem no lado esquerdo da caixa de diálogo Gerenciador de referências. Cada provedor contém todas as informações necessárias para a caixa de diálogo popular e exibir os dados necessários para adicionar uma referência ao seu projeto.  
  
 A ilustração a seguir resume o processo.  
  
 ![Configurando o Gerenciador de referência](../misc/media/refmgrextend.png "RefMgrExtend")  
  
 ![Configurando o Gerenciador de referência](../misc/media/refmgrextend2.png "RefMgrExtend2")  
  
## Adicionar uma guia personalizada  
 Para adicionar uma guia personalizada, você deve implementar um IReferenceProvider, um IVsReference e um IVsReferenceProviderContext.  
  
#### Para adicionar uma guia personalizada  
  
1.  Implementar a interface IReferenceProvider e, em seguida, exportá\-lo por meio do Managed Extensibility Framework \(MEF\) para o Gerenciador de referência para usar.  
  
     O Gerenciador de referência usa o objeto ReferenceProvider para gerar os itens que aparecem no Gerenciador de referências. A interface para esse objeto é definida em Microsoft.VisualStudio.ReferenceManager.Contracts.dll.  
  
2.  Implemente um objeto ProviderContext.  
  
     O Gerenciador de referência usa a propriedade GUID desse objeto para corresponder o contexto para o provedor. Quando inicializa o Gerenciador de referências, ele passa o provedor a ProviderContext que é passado pelo método ShowReferenceManager. O ProviderContext deve conter todas as informações que o provedor deve enumerar IVsReferences.  
  
3.  Estenda a classe StandardReferenceProviderContext.  
  
     O Gerenciador de referência fornece algumas classes base, como a classe StandardReferenceProviderContext, que você pode usar para começar. Sua classe de provedor pode estender StandardReferenceProvider, e o item de referência pode estender StandardReferenceItem.  
  
 A classe de provedor pode parecer com este exemplo:  
  
```  
[Export(typeof(IReferenceProvider))] [ExportMetadata("Name", "AssemblyReferenceProvider")] [ExportMetadata("Guid", VSConstants.AssemblyReferenceProvider_string)] internal class AssemblyReferenceProvider : StandardReferenceProvider { }  
```  
  
 Sua classe de contexto pode parecer com este exemplo:  
  
```  
  
[Export(typeof(IVsReferenceProviderContext))] [Export(typeof(IVsAssemblyReferenceProviderContext))] [Export("AssemblyReferenceProviderContext", typeof(IVsReferenceProviderContext))] [Export(VSConstants.AssemblyReferenceProvider_string, typeof(IVsReferenceProviderContext))] [PartCreationPolicy(System.ComponentModel.Composition.CreationPolicy.NonShared)] [ExportMetadata("Name", "AssemblyReferenceProviderContext")] [ExportMetadata("Guid", VSConstants.AssemblyReferenceProvider_string)] public class AssemblyReferenceProviderContext : StandardReferenceProviderContext<IVsAssemblyReference, AssemblyIdentity>, IVsAssemblyReferenceProviderContext { }  
```  
  
 Para a sua classe de item de referência, é recomendável que você implemente IWatchableReference e tornar sua classe serializável. Ao seguir essa abordagem, você pode tirar proveito dos métodos de serialização de cache na classe StandardReferenceProvider, além do serviço ReferenceWatcher, que sincroniza automaticamente as verificações de item entre várias guias na caixa de diálogo:  
  
```  
[Serializable] public class StandardReferenceItem : IWatchableReference { }  
```  
  
 A classe ReferenceProvider contém dois métodos importantes. O primeiro método é Initialize, que é chamado apenas uma vez, quando o provedor é primeiro carregado na caixa de diálogo. O segundo método é SetContext, que é chamado imediatamente após a inicialização, mas pode ser chamado novamente, se os sistemas de projeto não adicionar as referências que você especificou e tentou confirmar.  
  
> [!NOTE]
>  Como provedores de persistem para a duração do programa, que possam salvar o estado entre as sessões, mas as condições de corrida podem ocorrer se o usuário fecha a caixa de diálogo e, em seguida, reabra\-lo rapidamente.  
  
## Substituir a fonte existente da enumeração de guia  
 Alguns contextos de provedor têm uma propriedade chamada guias, cujo tipo é uint. Essa propriedade é um bitmask e exibe seu controle de valores que guias esse provedor.  Por exemplo, a interface IVsAssemblyReferenceProviderContext define uma propriedade de guias, que pode ser definida com os seguintes valores:  
  
```  
namespace Microsoft.VisualStudio.Shell.Interop { public enum __VSASSEMBLYPROVIDERTAB { TAB_ASSEMBLY_FRAMEWORK = 1, TAB_ASSEMBLY_EXTENSIONS = 2, TAB_ASSEMBLY_ALL = 3, } }  
```  
  
 A classe IVsPlatformReferenceProviderContext tem uma propriedade semelhante. Você não pode alterar o nome da guia, mas você pode controlar o texto do cabeçalho que aparece quando o usuário escolhe a guia. Você pode controlar esse valor por meio dos métodos a seguir na classe IVsAssemblyProviderContext:  
  
```  
void SetTabTitle(uint etabId, string szTabTitle);  
```  
  
## Substituir o filtro na caixa de diálogo de procura  
 Você pode fornecer um filtro de tipo personalizado à caixa de diálogo Procurar no Gerenciador de referências, alterando o valor da propriedade BrowseFilter no objeto IFileReferenceProviderContext.  O exemplo a seguir demonstra essa técnica de código nativo:  
  
```  
  
// Holds a list of provider contexts CComSafeArray<LPUNKNOWN> spProviderContexts; // Creates the file reference context for Browse vsReferenceManager->CreateProviderContext(GUID_FileReferenceProvider, &pFileRefProviderContext)); // Sets the Browse filter pFileRefProviderContext->put_BrowseFilter(wszFilter); spProviderContexts.Add(pFileRefProviderContext); // Show the reference manager hr = srpRefMgr->ShowReferenceManager( spVsRefMgrUser, spProviderContexts, strTitle, HELPKEYWORD_AddReference, GUID_AssemblyReferenceProvider, wszFilter, m_bstrStartBrowse);  
```  
  
## Consulte também  
 [Como: Adicionar ou remover referências usando o Gerenciador de Referências](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)