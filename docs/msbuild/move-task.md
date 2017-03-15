---
title: Tarefa Move | Microsoft Docs
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
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
ms.openlocfilehash: 19019bfbc0a731f566e1ffd13fa30dd497eb0f96
ms.lasthandoff: 02/22/2017

---
# <a name="move-task"></a>Tarefa Move
Move os arquivos para um novo local.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Move`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`DestinationFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica a lista de arquivos para a qual os arquivos de origem serão movidos. Essa lista deve ser um mapeamento um-para-um para a lista especificada no parâmetro `SourceFiles`. Ou seja, o primeiro arquivo especificado em `SourceFiles` será movido para o primeiro local especificado em `DestinationFiles` e assim por diante.|  
|`DestinationFolder`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o diretório para o qual você deseja mover os arquivos.|  
|`MovedFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que foram movidos com êxito.|  
|`OverwriteReadOnlyFiles`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, substitua arquivos mesmo se eles estiverem marcados como arquivos somente leitura.|  
|`SourceFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos a serem movidos.|  
  
## <a name="remarks"></a>Comentários  
 Um dos parâmetros `DestinationFolder` ou `DestinationFiles` deve ser especificado, mas não ambos. Se os dois forem especificados, a tarefa falhará e um erro será registrado.  
  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
