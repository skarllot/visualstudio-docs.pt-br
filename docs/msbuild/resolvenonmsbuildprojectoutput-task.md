---
title: Tarefa ResolveNonMSBuildProjectOutput | Microsoft Docs
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
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
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
ms.openlocfilehash: 34622d9b32933fc9c663c78b6f058fe46eed36c0
ms.lasthandoff: 02/22/2017

---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Tarefa ResolveNonMSBuildProjectOutput
Determina os arquivos de saída para referências de projeto não MSBuild.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `ResolveNonMSBuildProjectOutput`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Parâmetro `String` opcional.<br /><br /> Especifica uma cadeia de caracteres XML que contém saídas de projeto resolvidas.|  
|`ProjectReferences`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica as referências do projeto.|  
|`ResolvedOutputPaths`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de caminhos de referência resolvidos (e preserva os atributos de referência do projeto original).|  
|`UnresolvedProjectReferences`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de itens de referência de projeto que não puderam ser resolvidos usando a lista pré-resolvida de saídas.<br /><br /> Como o Visual Studio só pré-resolve projetos não MSBuild, isso significa que as referências de projeto nesta lista estão no formato MSBuild.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
