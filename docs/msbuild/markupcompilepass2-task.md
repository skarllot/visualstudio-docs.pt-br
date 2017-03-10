---
title: "Tarefa MarkupCompilePass2 | Microsoft Docs"
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
  - "Tarefa MarkupCompilePass2 [WPF MSBuild]"
  - "Tarefa MarkupCompilePass2 [WPF MSBuild], parâmetros"
  - "executando uma marcação de segunda passagem [WPF MSBuild], Tarefa MarkupCompilePass2"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa MarkupCompilePass2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tarefa executa a compilação da marcação de segundo passo em [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] arquivos que fazem referência a tipos no mesmo projeto.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcional  **Boolean** parâmetro.<br /><br /> Especifica se deseja executar a tarefa em um separado <xref:System.AppDomain>.  Se esse parâmetro retorna  **false**, a tarefa é executada na mesma <xref:System.AppDomain> como [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], e ele é executado mais rapidamente.  Se o parâmetro retorna  **true**, a tarefa é executada em um segundo <xref:System.AppDomain> que está isolado do [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] e fica mais lento.|  
|`AssembliesGeneratedDuringBuild`|Opcional  **String \[** parâmetro.<br /><br /> Especifica as referências aos assemblies alterados durante o processo de compilação.  Por exemplo, um [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] solução pode conter um projeto que faz referência a saída compilada de outro projeto.  Nesse caso, a saída compilada do projeto segundo pode ser adicionada a  **AssembliesGeneratedDuringBuild**.<br /><br /> Obs.:  **AssembliesGeneratedDuringBuild** deve conter referências ao conjunto completo de assemblies que são gerados por uma solução de compilação.|  
|`AssemblyName`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto.  Por exemplo, se um projeto está gerando um [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] executável cujo nome é  **WinExeAssembly.exe**, o  **AssemblyName** parâmetro tem um valor de  **WinExeAssembly**.|  
|`GeneratedBaml`|Opcional  **\[\] de ITaskItem** parâmetro de saída.<br /><br /> Contém a lista de arquivos gerados em [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] formato binário.|  
|`KnownReferencePaths`|Opcional  **String \[** parâmetro.<br /><br /> Especifica as referências aos assemblies que nunca são alteradas durante o processo de compilação.  Inclui assemblies localizados na [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], em um [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] diretório de instalação e assim por diante.|  
|`Language`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica que o compilador suporta linguagem gerenciada.  As opções válidas são  **C\#**,  **VB**,  **JScript**, e  **C\+\+**.|  
|`LocalizationDirectivesToLocFile`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica como gerar informações de localização para cada fonte de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo.  As opções válidas são  **Nenhum**,  **CommentsOnly**, e  **todos os**.|  
|`OutputPath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o diretório em que o gerado [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] serão gerados arquivos de formato binário.|  
|`OutputType`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o tipo de montagem que é gerado por um projeto.  As opções válidas são  **winexe**,  **exe**,  **biblioteca**, e  **netmodule**.|  
|`References`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a lista de referências de arquivos para assemblies que contêm os tipos que são usados na [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos.  É de uma referência ao assembly gerado pelo <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> tarefa, que deve ser executada antes do <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tarefa.|  
|`RootNamespace`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o namespace raiz para classes que estão dentro do projeto.  **RootNamespace** também é usado como o namespace padrão de um código gerenciado gerado arquivo quando o correspondente [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo não inclui o `x:Class` atributo.|  
|`XAMLDebuggingInformation`|Opcional  **Boolean** parâmetro.<br /><br /> Quando  **true**, informações de diagnóstico são geradas e incluídas no compilado [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] para depuração de auxílio.|  
  
## Comentários  
 Antes de executar  **MarkupCompilePass2**, você deve gerar um assembly temporário que contém os tipos que são usados pela [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos cuja passagem de compilação da marcação foram adiados.  Gerar o assembly temporário executando o  **GenerateTemporaryTargetAssembly** tarefa.  
  
 Uma referência ao assembly temporário gerado é fornecida para <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> quando ele é executado, permitindo que o [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos cuja compilação foi adiada na primeira compilação da marcação passam a ser compilado agora em formato binário.  
  
## Exemplo  
 O exemplo a seguir mostra como usar o <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tarefa para executar um segundo passar a compilação.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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