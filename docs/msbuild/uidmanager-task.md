---
title: "Tarefa UidManager | Microsoft Docs"
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
  - "verificando UIDs na localização de elementos XAML [WPF MSBuild]"
  - "localizando elementos XAML [WPF MSBuild], gerenciando UIDs"
  - "gerenciando UIDs na localização de elementos XAML [WPF MSBuild]"
  - "Tarefa UidManager [WPF MSBuild]"
  - "Tarefa UidManager [WPF MSBuild], parâmetros"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa UidManager
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.UidManager> tarefa verifica, atualiza ou remove os identificadores exclusivos \(UIDs\), para localizar todos os [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] elementos que estão incluídos na fonte de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`IntermediateDirectory`|Opcional  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o diretório que é usado para fazer backup de origem [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos que são especificados pelo  **MarkupFiles** parâmetro.|  
|`MarkupFiles`|Obrigatório  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica a fonte de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos a serem incluídos para UID de verificação, atualizar ou remover.|  
|`Task`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica a tarefa de gerenciamento de UID que você deseja executar.  As opções válidas são  **Check**,  **atualização**, ou  **Remover**.|  
  
## Exemplo  
 O exemplo a seguir usa a <xref:Microsoft.Build.Tasks.Windows.UidManager> tarefa para verificar que a fonte especificada [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos contêm [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] elementos que têm UIDs apropriados.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Como localizar um aplicativo](../Topic/How%20to:%20Localize%20an%20Application.md)