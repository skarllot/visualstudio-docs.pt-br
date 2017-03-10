---
title: "Tarefa MarkupCompilePass1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "convertendo projetos XAML no formato binário compilado [WPF MSBuild]"
  - "convertendo XAML no formato binário [WPF MSBuild]"
  - "Tarefa MarkupCompilePass1 [WPF MSBuild], convertendo XAML no formato binário"
  - "Tarefa MarkupCompilePass1 [WPF MSBuild], parâmetros"
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa MarkupCompilePass1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tarefa converte não localizáveis [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] arquivos em formato binário compilado do projeto.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AllGeneratedFiles`|Opcional  **\[\] de ITaskItem** parâmetro de saída.<br /><br /> Contém uma lista completa dos arquivos gerados pelo <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tarefa.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcional  **Boolean** parâmetro.<br /><br /> Especifica se deseja executar a tarefa em um separado <xref:System.AppDomain>.  Se esse parâmetro retorna  **false**, a tarefa é executada na mesma <xref:System.AppDomain> como [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] e ele é executado mais rapidamente.  Se o parâmetro retorna  **true**, a tarefa é executada em um segundo <xref:System.AppDomain> que está isolado do [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] e fica mais lento.|  
|`ApplicationMarkup`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica o nome da definição de aplicativo [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo.|  
|`AssembliesGeneratedDuringBuild`|Opcional  **String \[** parâmetro.<br /><br /> Especifica as referências aos assemblies alterados durante o processo de compilação.  Por exemplo, um [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] solução pode conter um projeto que faz referência a saída compilada de outro projeto.  Nesse caso, a saída compilada do segundo projeto pode ser adicionada para o  **AssembliesGeneratedDuringBuild** parâmetro.<br /><br /> Observação: O  **AssembliesGeneratedDuringBuild** parâmetro deve conter referências ao conjunto completo de assemblies que são gerados por uma solução de compilação.|  
|`AssemblyName`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto.  Por exemplo, se um projeto está gerando um [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] executável cujo nome é  **WinExeAssembly.exe**, o  **AssemblyName** parâmetro tem um valor de  **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o token de chave público para o assembly.|  
|`AssemblyVersion`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o número de versão do assembly.|  
|`ContentFiles`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a lista de arquivos de conteúdo flexível.|  
|`DefineConstants`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica que o valor atual de  **DefineConstants**, é mantido.  o que afeta a geração de assembly de destino; Se este parâmetro for alterado, a API pública do assembly de destino pode ser alterada e a compilação de [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] arquivos que fazem referência a tipos de locais podem ser afetados.|  
|`ExtraBuildControlFiles`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica uma lista de arquivos que controlam se uma reconstrução é acionado quando o <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tarefa reapresentações; uma reconstrução é disparada se um desses arquivos alterações.|  
|`GeneratedBamlFiles`|Opcional  **\[\] de ITaskItem** parâmetro de saída.<br /><br /> Contém a lista de arquivos gerados em [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] formato binário.|  
|`GeneratedCodeFiles`|Opcional  **\[\] de ITaskItem** parâmetro de saída.<br /><br /> Contém a lista de arquivos de código gerenciado gerado.|  
|`GeneratedLocalizationFiles`|Opcional  **\[\] de ITaskItem** parâmetro de saída.<br /><br /> Contém a lista de arquivos de localização que foram gerados para cada localizáveis [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo.|  
|`HostInBrowser`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica se o assembly gerado é um [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  As opções válidas são  **true** e  **false**.  Se  **true**, o código é gerado para dar suporte à hospedagem do navegador.|  
|`KnownReferencePaths`|Opcional  **String \[** parâmetro.<br /><br /> Especifica as referências aos assemblies que não são alterados durante o processo de compilação.  Inclui assemblies localizados na [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], em um [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] diretório de instalação e assim por diante.|  
|`Language`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica que o compilador suporta linguagem gerenciada.  As opções válidas são  **C\#**,  **VB**,  **JScript**, e  **C\+\+**.|  
|`LanguageSourceExtension`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica a extensão que é acrescentada à extensão do arquivo gerado código gerenciado:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Se a  **LanguageSourceExtension** parâmetro não estiver definido com um valor específico, a extensão de nome de arquivo de fonte padrão para um idioma é usada:  **. vb** para [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)],  **.csharp** para [!INCLUDE[TLA#tla_cshrp](../msbuild/includes/tlasharptla_cshrp_md.md)].|  
|`LocalizationDirectivesToLocFile`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica como gerar informações de localização para cada fonte de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo.  As opções válidas são  **Nenhum**,  **CommentsOnly**, e  **todos os**.|  
|`OutputPath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o diretório em que o gerado de arquivos de código gerenciado e [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] serão gerados arquivos de formato binário.|  
|`OutputType`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o tipo de montagem que é gerado por um projeto.  As opções válidas são  **winexe**,  **exe**,  **biblioteca**, e  **netmodule**.|  
|`PageMarkup`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica uma lista de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de arquivos para o processo.|  
|`References`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a lista de referências de arquivos para assemblies que contêm os tipos que são usados na [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos.|  
|`RequirePass2ForMainAssembly`|Opcional  **Boolean** parâmetro de saída.<br /><br /> Indica se o projeto contém não localizáveis [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos que fazem referência a tipos de locais que são incorporados ao assembly principal.|  
|`RequirePass2ForSatelliteAssembly`|Opcional  **Boolean** parâmetro de saída.<br /><br /> Indica se o projeto contém localizáveis [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos que fazem referência a tipos de locais que são incorporados no assembly principal.|  
|`RootNamespace`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o namespace raiz para classes que estão dentro do projeto.  **RootNamespace** também é usado como o namespace padrão de um código gerenciado gerado arquivo quando o correspondente [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo não inclui o `x:Class` atributo.|  
|`SourceCodeFiles`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a lista de arquivos de código para o projeto atual.  A lista não inclui os arquivos gerados específicos do idioma de código gerenciado.|  
|`UICulture`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o assembly satélite para a cultura da interface do usuário em que o gerado [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] são incorporados a arquivos de formato binário.  Se  **UICulture** não estiver definido, o gerado [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos de formato binário são incorporados no assembly principal.|  
|`XAMLDebuggingInformation`|Opcional  **Boolean** parâmetro.<br /><br /> Quando  **true**, informações de diagnóstico são geradas e incluídas no compilado [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] para depuração de auxílio.|  
  
## Comentários  
 O <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tarefa normalmente compila [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em formato binário e gera arquivos de código.  Se um [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo contém referências aos tipos que são definidos no mesmo projeto, a sua compilação em formato binário é adiada por  **MarkupCompilePass1** para uma segunda passagem de compilação de marcação \(**MarkupCompilePass2**\).  Esses arquivos devem ter seu compilação adiada porque eles devem aguardar os tipos referenciados definidas localmente são compilados.  No entanto, se um [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] o arquivo tem um `x:Class` atributo, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> gera o arquivo de código de idioma específico para ele.  
  
 A [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo é localizável, se ele contiver elementos que usam o `x:Uid` atributo:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 A [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo faz referência a um tipo definido localmente quando ele declara um [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] namespace que usa a `clr-namespace` valor para se referir a um espaço para nome no projeto atual:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 Se houver [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo é localizável, ou faz referência a um tipo definido localmente, uma segunda passagem de compilação de marcação é necessária, que requer a execução de [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) e, em seguida o [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## Exemplo  
 O exemplo a seguir mostra como converter três `Page`[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos para arquivos de formato binário.  `Page1`contém uma referência a um tipo, `Class1`, que está no namespace raiz do projeto e, portanto, não é convertido em arquivos de formato binário nesse passo de compilação da marcação.  Em vez disso, o [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) é executado e é seguido de [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Visão geral dos aplicativos de navegador XAML do WPF](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)