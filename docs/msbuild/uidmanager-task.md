---
title: Tarefa UidManager | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 49d154f8f64bbd61483396f2e6172113f6d8c86f
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
# <a name="uidmanager-task"></a>Tarefa UidManager
A tarefa <xref:Microsoft.Build.Tasks.Windows.UidManager> verifica, atualiza ou remove UIDs (identificadores exclusivos), para localizar todos os elementos [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] que são incluídos nos arquivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de origem.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`IntermediateDirectory`|Parâmetro **String** opcional.<br /><br /> Especifica o diretório usado para fazer backup dos arquivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de origem especificados pelo parâmetro **MarkupFiles**.|  
|`MarkupFiles`|Parâmetro obrigatório **ITaskItem[]**.<br /><br /> Especifica os arquivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de origem que serão incluídos na verificação, atualização ou remoção de UID.|  
|`Task`|Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica a tarefa de gerenciamento de UID que você deseja executar. As opções válidas são **Verificar**, **Atualizar** ou **Remover**.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa <xref:Microsoft.Build.Tasks.Windows.UidManager> para verificar se os arquivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de origem contêm elementos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] que têm UIDs apropriados.  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Referência MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Como compilar um aplicativo WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Como: localizar um aplicativo](/dotnet/framework/wpf/advanced/how-to-localize-an-application)
