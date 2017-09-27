---
title: "A geração em um processo de compilação de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 28
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 6cfdd28afbfb88f83d7931b57adbedfb88bf93bf
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="code-generation-in-a-build-process"></a>Geração de código em um processo de build
[Transformação de texto](../modeling/code-generation-and-t4-text-templates.md) pode ser chamado como parte do [do processo de compilação](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução. Há tarefas de compilação que são especializadas para a transformação de texto. As tarefas de compilação T4 executam modelos de texto de tempo de design e também compilam modelos de texto de tempo de execução (pré-processados).  
  
 Há algumas diferenças em termos do que as tarefas de compilação podem fazer, dependendo do mecanismo de compilação que você usa. Quando você compila a solução no Visual Studio, um modelo de texto pode acessar a API do Visual Studio (EnvDTE) se o [hostspecific = "true"](../modeling/t4-template-directive.md) atributo está definido. Mas isso não é verdadeiro quando você compila a solução da linha de comando ou quando você iniciar uma compilação do servidor por meio do Visual Studio. Nesses casos, a compilação é executada pelo MSBuild e um host T4 diferente é usado.  
  
 Isso significa que você não pode acessar coisas como nomes de arquivo de projeto da mesma forma quando você cria um modelo de texto no MSBuild. No entanto, você pode [passar informações de ambiente para modelos de texto e os processadores de diretiva usando parâmetros de compilação](#parameters).  
  
##  <a name="buildserver"></a>Configurar as máquinas  
 Para habilitar tarefas de compilação no computador de desenvolvimento, instale o SDK de modelagem para Visual Studio.
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

 Se [seu servidor de compilação](http://msdn.microsoft.com/Library/788443c3-0547-452e-959c-4805573813a9) é executado em um computador no qual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não é estiver instalado, copie os seguintes arquivos para o computador de compilação do seu computador de desenvolvimento. Substituir os números de versão mais recentes de ' *'.  
  
-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating  
  
    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll  
  
    -   Microsoft.TextTemplating.Build.Tasks.dll  
  
    -   Microsoft.TextTemplating.targets  
  
-   $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0  
  
    -   Microsoft.VisualStudio.TextTemplating.*.0.dll  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (vários arquivos)  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll  
  
-   $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll  
  
## <a name="to-edit-the-project-file"></a>Para editar o arquivo do projeto  
 Você precisará editar o arquivo de projeto para configurar alguns dos recursos no MSBuild.  
  
 No Gerenciador de soluções, escolha **Unload** no menu de contexto do projeto. Isso permite que você edite o arquivo .csproj ou .vbproj no editor de XML.  
  
 Quando você terminar de editar, escolha **recarregar**.  
  
## <a name="import-the-text-transformation-targets"></a>Importar os destinos da transformação de texto  
 No arquivo .vbproj ou .csproj, localize uma linha como esta:  
  
 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`  
  
 \- ou -  
  
 `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`  
  
 Depois dessa linha, insira a importação de modelagem de texto:  
  
```xml  
<!-- Optionally make the import portable across VS versions -->  
  <PropertyGroup>  
    <!-- Get the Visual Studio version - defaults to 10: -->  
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>  
    <!-- Keep the next element all on one line: -->  
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>  
  </PropertyGroup>  
  
<!-- This is the important line: -->  
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />  
```  
  
## <a name="transforming-templates-in-a-build"></a>Transformando modelos em uma compilação  
 Há algumas propriedades que podem ser inseridas em seu arquivo de projeto para controlar a tarefa de transformação:  
  
-   Execute a tarefa Transform no início de cada compilação:  
  
    ```xml  
    <PropertyGroup>  
        <TransformOnBuild>true</TransformOnBuild>  
    </PropertyGroup>  
    ```  
  
-   Substitua os arquivos que são somente leitura, por exemplo, porque eles não passam por check-out:  
  
    ```xml  
    <PropertyGroup>  
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>  
    </PropertyGroup>  
    ```  
  
-   Transforme cada modelo toda vez:  
  
    ```xml  
    <PropertyGroup>  
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>  
    </PropertyGroup>  
    ```  
  
     Por padrão, a tarefa T4 do MSBuild gera um arquivo de saída se for mais antigo que seu arquivo de modelo, ou que qualquer arquivo incluído ou lido anteriormente pelo modelo ou por um processador de diretriz que ele use. Observe que esse é um teste de dependência muito mais avançado do que é usado pelo comando Transformar Todos os Modelos no Visual Studio, que compara apenas as datas do modelo e do arquivo de saída.  
  
 Para executar apenas as transformações de texto em seu projeto, invoque a tarefa TransformAll:  
  
 `msbuild myProject.csproj /t:TransformAll`  
  
 Para transformar um modelo específico de texto:  
  
 `msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`  
  
 Você pode usar curingas em TransformFile:  
  
 `msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`  
  
## <a name="source-control"></a>Controle do código-Fonte  
 Não há integração interna específica com um sistema de controle do código-fonte. No entanto, você pode adicionar suas próprias extensões, por exemplo, para fazer check-out e check-in de um arquivo gerado. Por padrão, a tarefa de transformação de texto impede que um arquivo seja marcado como somente leitura e, quando esse arquivo é localizado, um erro é registrado na lista de erros do Visual Studio e a tarefa falha.  
  
 Para especificar que os arquivos somente leitura devem ser substituídos, insira esta propriedade:  
  
 `<OverwriteReadOnlyOuputFiles>true</OverwriteReadOnlyOuputFiles>`  
  
 A menos que você personalize a etapa de pós-processamento, um aviso será registrado na lista de erros quando um arquivo for substituído.  
  
## <a name="customizing-the-build-process"></a>Personalizando o processo de compilação  
 A transformação de texto ocorre antes de outras tarefas no processo de compilação. Você pode definir as tarefas que são invocadas antes e depois da transformação, definindo as propriedades `$(BeforeTransform)` e `$(AfterTransform)`:  
  
```  
<PropertyGroup>  
    <BeforeTransform>CustomPreTransform</BeforeTransform>  
    <AfterTransform>CustomPostTransform</AfterTransform>  
  </PropertyGroup>  
  <Target Name="CustomPreTransform">  
    <Message Text="In CustomPreTransform..." Importance="High" />  
  </Target>  
  <Target Name="CustomPostTransform">  
    <Message Text="In CustomPostTransform..." Importance="High" />  
  </Target>  
```  
  
 Em `AfterTransform`, você pode referenciar listas de arquivos:  
  
-   GeneratedFiles – uma lista de arquivos gravados pelo processo. Para os arquivos que substituíram os arquivos somente leitura existentes, %(GeneratedFiles.ReadOnlyFileOverwritten) será true. Esses arquivos podem passar por check-out do controle do código-fonte.  
  
-   NonGeneratedFiles – uma lista de arquivos somente leitura que não foram substituídos.  
  
 Por exemplo, você definirá uma tarefa fazer check-out de GeneratedFiles.  
  
## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath e OutputFileName  
 Essas propriedades são usadas somente pelo MSBuild. Elas não afetam a geração de código no Visual Studio. Elas redirecionam o arquivo de saída gerado para uma pasta ou um arquivo diferente. A pasta de destino já deve existir.  
  
```xml  
<ItemGroup>  
  <None Include="MyTemplate.tt">  
    <Generator>TextTemplatingFileGenerator</Generator>  
    <OutputFilePath>MyFolder</OutputFilePath>  
    <LastGenOutput>MyTemplate.cs</LastGenOutput>  
  </None>  
</ItemGroup>  
```  
  
 Uma pasta útil para redirecionar é `$(IntermediateOutputPath).`  
  
 Se você especificar o nome do arquivo de saída, ele terá precedência sobre a extensão especificada na diretiva de saída nos modelos.  
  
```xml  
<ItemGroup>  
  <None Include="MyTemplate.tt">  
    <Generator>TextTemplatingFileGenerator</Generator>  
    <OutputFileName>MyOutputFileName.cs</OutputFileName>  
    <LastGenOutput>MyTemplate.cs</LastGenOutput>  
  </None>  
</ItemGroup>  
```  
  
 Especificando um OutputFileName ou OutputFilePath não é recomendado se você também estiver transformando modelos dentro do VS usando transformar All ou executar o gerador de arquivo único. Você acabará com caminhos de arquivos diferentes dependendo de como tiver desencadeado a transformação. Isso pode ser muito confuso.  
  
## <a name="adding-reference-and-include-paths"></a>Adicionando referência e incluir caminhos  
 O host tem um conjunto padrão de caminhos em que procura assemblies referenciados em modelos. Para adicionar a este conjunto:  
  
```  
<ItemGroup>  
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />  
    <!-- Add more T4ReferencePath items here -->  
</ItemGroup>  
```  
  
 Para definir as pastas em que arquivos de inclusão serão procurados, forneça uma lista separada por ponto-e-vírgula. Normalmente, você adiciona à lista de pastas existente.  
  
```  
<PropertyGroup>  
    <IncludeFolders>  
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>  
</PropertyGroup>  
  
```  
  
##  <a name="parameters"></a>Passar dados de contexto de compilação para os modelos  
 Você pode definir valores de parâmetros no arquivo do projeto. Por exemplo, você pode passar [criar](../msbuild/msbuild-properties.md) propriedades e [variáveis de ambiente](../msbuild/how-to-use-environment-variables-in-a-build.md):  
  
```xml  
<ItemGroup>  
  <T4ParameterValues Include="ProjectFolder">  
    <Value>$(ProjectDir)</Value>  
    <Visible>false</Visible>  
  </T4ParameterValues>  
</ItemGroup>  
```  
  
 Em um modelo de texto, defina `hostspecific` na diretiva do modelo. Use o [parâmetro](../modeling/t4-parameter-directive.md) diretiva para obter valores:  
  
```  
<#@template language="c#" hostspecific="true"#>  
<#@ parameter type="System.String" name="ProjectFolder" #>  
The project folder is: <#= ProjectFolder #>  
  
```  
  
 Em um processador de diretriz, você pode chamar <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>:  
  
```csharp  
string value = Host.ResolveParameterValue("-", "-", "parameterName");  
```  
  
```vb  
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")  
```  
  
> [!NOTE]
>  `ResolveParameterValue` obtém dados de `T4ParameterValues` somente quando você usa o MSBuild. Quando você transformar o modelo usando o Visual Studio, os parâmetros terão valores padrão.  
  
##  <a name="msbuild"></a>Usando as propriedades do projeto no assembly e as diretivas de inclusão  
 Macros do Visual Studio como $ (solutiondir) não funcionam no MSBuild. Você pode usar as propriedades do projeto como alternativa.  
  
 Edite seu arquivo .csproj ou .vbproj para definir uma propriedade do projeto. Este exemplo define uma propriedade chamada `myLibFolder`:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Agora você pode usar sua propriedade de projeto no assembly e diretivas de inclusão:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>  
```  
  
 Essas diretivas obtêm valores de T4parameterValues nos hosts do MSBuild e do Visual Studio.  
  
## <a name="q--a"></a>Perguntas e respostas  
 **Por que eu desejaria transformar modelos no servidor de compilação? Eu já transformou modelos no Visual Studio antes de que verifiquei meu código.**  
  
 Se você atualizar um arquivo incluído, ou em outro arquivo de leitura pelo modelo, o Visual Studio não transformar automaticamente o arquivo. Transformando modelos como parte da compilação assegura que tudo está atualizado.  
  
 **Quais outras opções são existe para transformar modelos de texto?**  
  
-   O [utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) podem ser usados em scripts de comando. Na maioria dos casos, é mais fácil de usar o MSBuild.  
  
-   [Invocando transformação de texto em uma extensão do VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
  
-   [Modelos de texto de tempo de design](../modeling/design-time-code-generation-by-using-t4-text-templates.md) são transformadas pelo Visual Studio.  
  
-   [Modelos de texto de tempo de execução](../modeling/run-time-text-generation-with-t4-text-templates.md) são transformadas em tempo de execução em seu aplicativo.  
  
## <a name="read-more"></a>Leia mais  
 Há uma boa orientação no modelo T4 do MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets  
  
 [Gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md)  
  
 [Oleg Sych: Noções básicas sobre integração T4:MSBuild](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


