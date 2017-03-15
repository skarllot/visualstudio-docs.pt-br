---
title: Usando o Visual Studio ModelBus em um modelo de texto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: a5a87537481c45ae5bc2746f0e056d636afa4fd8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Usando o Visual Studio ModelBus em um modelo de texto
Se você escrever modelos de texto que ler um modelo que contenha [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus referencia, talvez você queira resolver as referências para acessar os modelos de destino. Nesse caso, você deve adaptar os modelos de texto e as linguagens específicas de domínio referenciadas (DSLs):  
  
-   A DSL é o destino de referências deve ter um adaptador do ModelBus configurado para acesso a partir de modelos de texto. Se você também pode acessar a DSL de outro código, o adaptador reconfigurado é necessário além do padrão adaptador do ModelBus.  
  
     O Gerenciador de adaptador deve herdar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>e deve ter o atributo `[HostSpecific(HostName)]`.</xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>  
  
-   O modelo deve herdar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.</xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>  
  
> [!NOTE]
>  Se você quiser ler modelos DSL que não contêm referências do ModelBus, você pode usar os processadores de diretriz que são gerados em seus projetos DSL. Para obter mais informações, consulte [acessar modelos de modelos de texto](../modeling/accessing-models-from-text-templates.md).  
  
 Para obter mais informações sobre modelos de texto, consulte [geração de código de tempo de Design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Criando um adaptador de barramento de modelo para acesso a partir de modelos de texto  
 Para resolver uma referência do ModelBus em um modelo de texto, DSL de destino deve ter um adaptador compatível. Executar modelos de texto em um AppDomain separado do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documento editores e, portanto, o adaptador precisa carregar o modelo em vez de acessá-lo por meio de DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Para criar um adaptador do ModelBus compatível com modelos de texto  
  
1.  Se a solução DSL de destino não possui um **ModelBusAdapter** de projeto, crie uma usando o Assistente de extensão do Modelbus:  
  
    1.  Baixe e instale o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus extensão, se você ainda não tiver feito isso. Para obter mais informações, consulte [SDK de visualização e modelagem](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Abra o arquivo de definição de DSL. Clique na superfície de design e, em seguida, clique em **habilitar Modelbus**.  
  
    3.  Na caixa de diálogo, selecione **desejo expor essa DSL ao ModelBus**. Você pode selecionar as duas opções, se você quiser que essa DSL exponha seus modelos e consuma referências a outras DSLs.  
  
    4.  Clique em **OK**. Um novo projeto "ModelBusAdapter" é adicionado à solução de DSL.  
  
    5.  Clique em **transformar todos os modelos**.  
  
    6.  Recompile a solução.  
  
2.  Se você quiser acessar a DSL a partir de um modelo de texto e de outro código, como o comando, duplicar o **ModelBusAdapter** projeto:  
  
    1.  No Windows Explorer, copie e cole a pasta que contém **ModelBusAdapter.csproj**.  
  
    2.  Renomeie o arquivo de projeto (por exemplo, para **T4ModelBusAdapter.csproj**).  
  
    3.  Em **Solution Explorer**, com o botão direito no nó da solução, aponte para **adicionar**e, em seguida, clique em **projeto existente**. Localize o novo projeto do adaptador, **T4ModelBusAdapter.csproj**.  
  
    4.  Em cada `*.tt` arquivo do novo projeto, altere o namespace.  
  
    5.  Clique com botão direito no novo projeto no Solution Explorer e, em seguida, clique em Propriedades. No editor de propriedades, altere os nomes de assembly gerado e o namespace padrão.  
  
    6.  No projeto DslPackage, adicione uma referência para o novo projeto do adaptador para que ele tenha referências aos dois adaptadores.  
  
    7.  No DslPackage\source.extension.tt, adicione uma linha que referencia o novo projeto do adaptador.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Transformar todos os modelos** e recompile a solução. Nenhum erro de compilação deve ocorrer.  
  
3.  No novo projeto do adaptador, adicione referências aos assemblies a seguir:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  Em AdapterManager.tt:  
  
    -   Altere a declaração do AdapterManagerBase para que ela herde de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.</xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   No final do arquivo, substitua o atributo HostSpecific antes da classe AdapterManager. Remova a linha a seguir:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Insira a seguinte linha:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Esse atributo filtra o conjunto de adaptadores que estão disponível quando um consumidor modelbus procura um adaptador.  
  
5.  **Transformar todos os modelos** e recompile a solução. Nenhum erro de compilação deve ocorrer.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Gravando um modelo de texto que possa resolver referências do ModelBus  
 Normalmente, comece com um modelo que lê e gera arquivos de uma DSL de "origem". Este modelo usa a diretiva que é gerada no projeto DSL de origem para ler arquivos de modelo de origem da maneira descrita na [acessar modelos de modelos de texto](../modeling/accessing-models-from-text-templates.md). No entanto, a DSL de origem contém referências do ModelBus em um DSL "destino". Portanto, você deseja habilitar o código de modelo resolver as referências e acessar a DSL de destino. Portanto você deve adaptar o modelo seguindo estas etapas:  
  
-   Alterar a classe base do modelo para <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.</xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>  
  
-   Incluir `hostspecific="true"` na diretiva do modelo.  
  
-   Adicione referências de assembly DSL de destino e o seu adaptador e para habilitar ModelBus.  
  
-   A diretiva que é gerada como parte da DSL de destino não é necessário.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let’s assume they’re all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 Quando esse modelo de texto é executado, o `SourceDsl` diretiva carrega o arquivo `Sample.source`. O modelo pode acessar os elementos de modelo, a partir `this.ModelRoot`. O código pode usar as classes de domínio e propriedades que DSL.  
  
 Além disso, o modelo pode resolver referências do ModelBus. Quando as referências de apontarem para o modelo de destino, as diretivas de assembly permitem que o código use as propriedades do modelo DSL e classes de domínio.  
  
-   Se você não usar uma diretiva que é gerada por um projeto DSL, você também deve incluir o seguinte.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Use `this.ModelBus` para obter acesso ao ModelBus.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Passo a passo: Testando um modelo de texto que usa ModelBus  
 Neste passo a passo, você deve seguir estas etapas:  
  
1.  Construa duas DSLs. Uma DSL, o *consumidor*, tem um `ModelBusReference` propriedade que pode se referir a DSL, o *provedor*.  
  
2.  Crie dois adaptadores do ModelBus no provedor: uma para o acesso por modelos de texto, o outro para um código comum.  
  
3.  Crie modelos de instância das DSLs em um único projeto experimental.  
  
4.  Defina uma propriedade de domínio em um modelo para apontar para outro modelo.  
  
5.  Escreva um manipulador de clique duplo que abre o modelo que está apontado.  
  
6.  Escreva um modelo de texto que pode carregar o primeiro modelo, siga a referência a outro modelo e ler outro modelo.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Construir uma DSL que seja acessível para ModelBus  
  
1.  Crie uma nova solução DSL. Para este exemplo, selecione o modelo de solução fluxo de tarefa. O nome do idioma definido como `MBProvider` e a extensão de nome de arquivo para ".provide".  
  
2.  No diagrama de definição de DSL, clique em uma parte em branco do diagrama que não está na parte superior e, em seguida, clique em **habilitar Modelbus**.  
  
    -   Se você não vir **habilitar Modelbus**, você deve baixar e instalar a extensão do ModelBus VMSDK. Encontrá-lo no site do VMSDK: [SDK de visualização e modelagem](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  No **habilitar Modelbus** caixa de diálogo, selecione **expor essa DSL ao ModelBus**e, em seguida, clique em **Okey**.  
  
     Um novo projeto, `ModelBusAdapter`, é adicionado à solução.  
  
 Agora você tem uma DSL que pode ser acessada pelos modelos de texto por meio do ModelBus. As referências a ele podem ser resolvidas no código de comandos, manipuladores de eventos ou regras, que operam no AppDomain do editor de arquivo de modelo. No entanto, os modelos de texto executar em um AppDomain separado e não podem acessar um modelo quando ele está sendo editado. Se você desejar acessar referências do ModelBus para essa DSL de um modelo de texto, você deve ter um ModelBusAdapter separado.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Para criar um adaptador do ModelBus configurado para modelos de texto  
  
1.  No Windows Explorer, copie e cole a pasta que contém ModelBusAdapter.csproj.  
  
     Nomeie a pasta T4ModelBusAdapter.  
  
     Renomeie o arquivo de projeto T4ModelBusAdapter.csproj.  
  
2.  No Solution Explorer, adicione T4ModelBusAdapter à solução MBProvider. Clique com botão direito no nó da solução, aponte para **adicionar**e, em seguida, clique em **projeto existente**.  
  
3.  Clique com botão direito no nó do projeto T4ModelBusAdapter e, em seguida, clique em Propriedades. Na janela de propriedades do projeto, altere o **nome do Assembly** e **Namespace padrão** para `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  Em cada arquivo TT T4ModelBusAdapter, insira "T4" a última parte do namespace, para que a linha é semelhante ao seguinte.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  No `DslPackage` de projeto, adicione uma referência de projeto para `T4ModelBusAdapter`.  
  
6.  No DslPackage\source.extension.tt, adicione a seguinte linha sob `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  No `T4ModelBusAdapter` de projeto, adicione uma referência para: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Abra T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  Alterar a classe base do AdapterManagerBase para <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.</xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> Esta parte do arquivo agora é semelhante ao seguinte.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  No final do arquivo, insira o seguinte atributo adicional em frente à classe AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         O resultado é semelhante ao seguinte.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. Clique em **transformar todos os modelos** na barra de título do Solution Explorer.  
  
10. Recompile a solução. Clique em F5.  
  
11. Verificar se a DSL está funcionando pressionando F5. No projeto experimental, abra `Sample.provider`. Feche a instância experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Referências do ModelBus para essa DSL agora podem ser resolvidas em modelos de texto e também em código comum.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construir uma DSL com uma propriedade de domínio de referência do ModelBus  
  
1.  Crie uma nova DSL usando o modelo de solução de linguagem mínima. Nomeie a linguagem MBConsumer e definir a extensão de nome de arquivo para ".consume".  
  
2.  No projeto DSL, adicione uma referência ao assembly MBProvider DSL. Clique com botão direito `MBConsumer\Dsl\References` e, em seguida, clique em **adicionar referência**. No **procurar** guia, localize`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Isso permite que você crie o código que usa a DSL outra. Se você quiser criar referências para diversas DSLs, adicioná-los também.  
  
3.  No diagrama de definição de DSL, clique com botão direito do diagrama e, em seguida, clique em **habilitar ModelBus**. Na caixa de diálogo, selecione **habilitar esta DSL consumir o ModelBus**.  
  
4.  Na classe `ExampleElement`, adicionar uma nova propriedade de domínio `MBR`e na janela Propriedades, defina seu tipo como `ModelBusReference`.  
  
5.  Clique com botão direito a propriedade de domínio no diagrama e, em seguida, clique em **propriedades específicas do ModelBusReference editar**. Na caixa de diálogo, selecione **um elemento de modelo**.  
  
     Defina o filtro da caixa de diálogo de arquivo, como a seguir.  
  
     `Provider File|*.provide`  
  
     A subcadeia de caracteres depois de "|" é um filtro para a caixa de diálogo de seleção de arquivo. Você pode configurá-lo para permitir que todos os arquivos usando *.\*  
  
     No **o tipo de elemento de modelo** , digite os nomes de classes de domínio mais de uma ou no provedor de DSL (por exemplo, Company.MBProvider.Task). Eles podem ser classes abstratas. Se você deixar a lista, o usuário pode definir a referência a qualquer elemento.  
  
6.  Feche a caixa de diálogo e **transformar todos os modelos**.  
  
 Você criou uma DSL que pode conter referências a elementos em outra DSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Criar uma referência do ModelBus em outro arquivo na solução  
  
1.  Na solução MBConsumer, pressione CTRL + F5. Uma instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] abre no **MBConsumer\Debugging** projeto.  
  
2.  Adicione uma cópia do Sample.provide para o **MBConsumer\Debugging** projeto. Isso é necessário porque uma referência do ModelBus deve se referir a um arquivo na mesma solução.  
  
    1.  Clique com botão direito no projeto de depuração, aponte para **adicionar**e, em seguida, clique em **Item existente**.  
  
    2.  No **Adicionar Item** caixa de diálogo, defina o filtro **todos os arquivos (\*.\*) **.  
  
    3.  Navegue até `MBProvider\Debugging\Sample.provide` e, em seguida, clique em **adicionar**.  
  
3.  Abra `Sample.consume`.  
  
4.  Clique em uma forma de exemplo e na janela Propriedades, clique em **[...] ** na propriedade MBR. Na caixa de diálogo, clique em **procurar** e selecione `Sample.provide`. Na janela de elementos, expanda o tipo de tarefa e selecione um dos elementos.  
  
5.  Salve o arquivo.  
  
     (Ainda não feche a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 Você criou um modelo que contém uma referência do ModelBus para um elemento em outro modelo.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Resolver uma referência do ModelBus em um modelo de texto  
  
1.  Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra um arquivo de modelo de texto de exemplo. Defina seu conteúdo conforme segue.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     Lembre-se também dos seguintes pontos:  
  
    1.  O `hostSpecific` e `inherits` atributos a `template` diretiva deve ser definida.  
  
    2.  O modelo de consumidor é acessado da maneira normal por meio do processador de diretriz que foi gerado em que DSL.  
  
    3.  As diretivas de assembly e importação devem ser capazes de acessar ModelBus e os tipos de provedor de DSL.  
  
    4.  Se você souber que MBRs muitos estão vinculados para o mesmo modelo, é melhor chamar CreateAdapter apenas uma vez.  
  
2.  Salve o modelo. Verifique se que o arquivo de texto resultante é semelhante ao seguinte.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Resolver uma referência do ModelBus em um manipulador de gestos  
  
1.  Feche a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se ele estiver em execução.  
  
2.  Adicione um arquivo chamado MBConsumer\Dsl\Custom.cs e defina seu conteúdo para o seguinte.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Pressione CTRL+F5.  
  
4.  Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra `Debugging\Sample.consume`.  
  
5.  Clique duas vezes em uma forma.  
  
     Se você tiver configurado o MBR no elemento, abre o modelo de referência e o elemento referenciado está selecionado.  
  
## <a name="see-also"></a>Consulte também  
 [Integrando modelos por meio do Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

