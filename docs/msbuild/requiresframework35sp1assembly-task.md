---
title: Tarefa RequiresFramework35SP1Assembly | Microsoft Docs
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
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: cb02256815fc2b09e8d85870be475043c446528e
ms.lasthandoff: 02/22/2017

---
# <a name="requiresframework35sp1assembly-task"></a>Tarefa RequiresFramework35SP1Assembly
Determina se o aplicativo requer o .NET Framework 3.5 SP1.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `RequiresFramework35SP1Assembly`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Assemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Define os assemblies referenciados no aplicativo.|  
|`CreateDesktopShortcut`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, cria um ícone de atalho na área de trabalho durante a instalação.|  
|`DeploymentManifestEntryPoint`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o nome do arquivo de manifesto para o aplicativo.|  
|`EntryPoint`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o assembly que deve ser executado quando o aplicativo for executado.|  
|`ErrorReportUrl`|Parâmetro `String` opcional.<br /><br /> Especifica o site que é exibido nas caixas de diálogo que são encontradas durante as instalações do ClickOnce.|  
|`Files`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica a lista de arquivos que serão implantados quando o aplicativo for publicado.|  
|`ReferencedAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Define os assemblies referenciados no projeto.|  
|`RequiresMinimumFramework35SP1`|Parâmetro de saída `Boolean` opcional.<br /><br /> Se `true`, o aplicativo requer o .NET Framework 3.5 SP1.|  
|`SigningManifests`|Parâmetro de saída `Boolean` opcional.<br /><br /> Se `true`, os manifestos do ClickOnce são assinados.|  
|`SuiteName`|Parâmetro `String` opcional.<br /><br /> Especifica o nome da pasta no menu **Iniciar** no qual o aplicativo será instalado.|  
|`TargetFrameworkVersion`|Parâmetro `String` opcional.<br /><br /> Especifica a versão do .NET Framework que o aplicativo direciona.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
