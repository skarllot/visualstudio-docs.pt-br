---
title: "Tarefa GenerateTemporaryTargetAssembly | Microsoft Docs"
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
  - "processo de compilação [WPF MSBuild], a página do XAML refere-se a um tipo declarado localmente"
  - "criando um assembly [WPF MSBuild], a página do XAML refere-se a um tipo declarado localmente"
  - "Tarefa GenerateTemporaryTargetAssembly [WPF MSBuild]"
  - "Tarefa GenerateTemporaryTargetAssembly [WPF MSBuild], parâmetros"
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GenerateTemporaryTargetAssembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> tarefa gera um assembly, se pelo menos um [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] página em um projeto referencia um tipo que seja declarado localmente nesse projeto.  O assembly gerado é removido após a conclusão do processo de compilação ou se o processo de compilação falhar.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AssemblyName`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto e também é o nome do assembly de destino que é gerado temporariamente.  Por exemplo, se um projeto gera um [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] executável cujo nome é  **WinExeAssembly.exe**, o  **AssemblyName** parâmetro tem um valor de  **WinExeAssembly**.|  
|`CompileTargetName`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o nome da [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] o destino que é usado para gerar assemblies de arquivos de código fonte.  O valor típico para  **CompileTargetName** é  **CoreCompile**.|  
|`CompileTypeName`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o tipo de compilação é executada pelo destino especificado pelo  **CompileTargetName** parâmetro.  Para o  **CoreCompile** o destino, esse valor é  **Compilar**.|  
|`CurrentProject`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o caminho completo da [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] arquivo de projeto para o projeto que requer um assembly de destino temporário.|  
|`GeneratedCodeFiles`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a lista de arquivos específicos do idioma de código gerenciado que foram geradas com a [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) tarefa.|  
|`IntermediateOutputPath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o diretório que o assembly de destino temporário é gerado.|  
|`MSBuildBinPath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica a localização do  **MSBuild. exe**, que é necessário para compilar o assembly de destino temporário.|  
|`ReferencePath`|Opcional  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica uma lista de assemblies, pelo caminho e nome de arquivo, que são referenciados pelos tipos que são compilados no assembly de destino temporário.|  
|`ReferencePathTypeName`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o parâmetro que é usado pelo destino de compilação \(**CompileTargetName**\) parâmetro especifica a lista de referências de assembly \(**ReferencePath**\).  O valor apropriado é  **ReferencePath**.|  
  
## Comentários  
 A primeira passagem de marcação de compilação, o que é executada, o [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compila [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos em formato binário.  Conseqüentemente, o compilador precisa de uma lista de assemblies referenciados que contêm os tipos que são usados pela [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos.  No entanto, se um [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivo usa um tipo que é definido no mesmo projeto, um assembly correspondente para o projeto não é criado até que o projeto é construído.  Portanto, uma referência de assembly não pode ser fornecida durante a primeira etapa de compilação da marcação.  
  
 Em vez disso,  **MarkupCompilePass1** adia a conversão de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos que contêm referências aos tipos no mesmo projeto para uma compilação da marcação segundo passam, o qual está sendo executada pelo [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  Antes de  **MarkupCompilePass2** é executado, um assembly temporário é gerado.  Este assembly contém os tipos que são usados pela [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos cuja passagem de compilação da marcação foi adiada.  Uma referência ao assembly gerado é fornecida para  **MarkupCompilePass2** quando ele é executado para permitir que a compilação adiada [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos a ser convertido em formato binário.  
  
## Exemplo  
 O exemplo a seguir gera um assembly temporário porque `Page1.xaml` contém uma referência a um tipo que esteja no mesmo projeto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
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