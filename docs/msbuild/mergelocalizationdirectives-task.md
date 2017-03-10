---
title: "Tarefa MergeLocalizationDirectives | Microsoft Docs"
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
  - "localizando o XAML [WPF MSBuild], movendo comentários e atributos para um arquivo separado"
  - "Tarefa MergeLocalizationDirectives [WPF MSBuild]"
  - "Tarefa MergeLocalizationDirectives [WPF MSBuild], parâmetros"
  - "movendo comentários de localização e atributos para um arquivo separado [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa MergeLocalizationDirectives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> tarefa mescla os atributos de localização e comentários de uma ou mais [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos de formato binário em um único arquivo para o assembly inteiro.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`GeneratedLocalizationFiles`|Obrigatório  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a lista de arquivos de diretivas de localização de arquivos individuais no [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] formato binário.|  
|`OutputFile`|Obrigatório  **seqüência de caracteres** parâmetro de saída.<br /><br /> Especifica o caminho de saída do assembly compilado de diretivas de localização.|  
  
## Comentários  
 Você pode adicionar atributos de localização e seus comentários para [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] conteúdo.  Com [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] suporte à localização, você pode retirar os atributos de localização e seus comentários e colocá\-los em um arquivo. loc separado do assembly gerado.  Você pode fazer isso usando o  **LocalizationPropertyStorage** atributo.  Para obter mais informações sobre atributos de localização e comentários, e  **LocalizationPropertyStorage**, consulte [Atributos de localização e comentários](../Topic/Localization%20Attributes%20and%20Comments.md).  
  
## Exemplo  
 O exemplo a seguir mescla os comentários de localização de vários [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos de formato binário em um arquivo. loc único.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)