---
title: Tarefa CreateCSharpManifestResourceName | Microsoft Docs
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 8
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
ms.openlocfilehash: 574e04aa1c741c0a1720adf3fc77c2765f9dc1d3
ms.lasthandoff: 02/22/2017

---
# <a name="createcsharpmanifestresourcename-task"></a>Tarefa CreateCSharpManifestResourceName
Cria um nome de manifesto de estilo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] de um nome de arquivo .resx fornecido ou de outro recurso.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da [tarefa CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ManifestResourceNames`|Parâmetro somente leitura de saída <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Os nomes de manifesto resultantes.|  
|`ResourceFiles`|Parâmetro `String` obrigatório.<br /><br /> O nome do arquivo de recurso do qual criar o nome do manifesto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].|  
|`RootNamespace`|Parâmetro `String` opcional.<br /><br /> O namespace raiz do arquivo de recurso, geralmente obtido do arquivo de projeto. Pode ser `null`.|  
|`PrependCultureAsDirectory`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, o nome da cultura é adicionado como um nome de diretório antes do nome do recurso de manifesto. O valor padrão é `true`.|  
|`ResourceFilesWithManifestResourceNames`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o nome do arquivo de recurso que agora inclui o nome do recurso de manifesto.|  
  
## <a name="remarks"></a>Comentários  
 A [tarefa CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina o nome do recurso de manifesto apropriado para atribuir a um determinado arquivo .resx ou outro arquivo de recurso. A tarefa fornece um nome lógico para um arquivo de recurso e, em seguida, anexa-o a um parâmetro de saída como metadados.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
