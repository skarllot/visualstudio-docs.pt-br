---
title: Tarefa ResolveNativeReference| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 9
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
ms.openlocfilehash: b0b08a9602c81e504bf2cd01d1d1ce9720dc6b2a
ms.lasthandoff: 02/22/2017

---
# <a name="resolvenativereference-task"></a>Tarefa ResolveNativeReference
Resolve referências nativas. Implementa a classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Essa classe dá suporte à infraestrutura do .NET Framework, que não se destina a ser usada diretamente do seu código.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `ResolveNativeReference`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Parâmetro obrigatório [String](assetId:///String?qualifyHint=False&autoUpgrade=True)`[]`.<br /><br /> Obtém ou define os caminhos de pesquisa para resolver as identidades de assembly de referências nativas.|  
|`ContainedComComponents`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os componentes COM do assembly nativo.|  
|`ContainedLooseEtcFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os arquivos Etc flexíveis listados no manifesto nativo.|  
|`ContainedLooseTlbFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os arquivos .tlb do assembly nativo.|  
|`ContainedPrerequisiteAssemblies`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os assemblies que devem estar presentes antes que o manifesto possa ser usado.|  
|`ContainedTypeLibraries`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define as bibliotecas de tipo do assembly nativo.|  
|`ContainingReferenceFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os arquivos de referência.|  
|`NativeReferences`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Obtém ou define as referências de assembly nativo do Win32.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
