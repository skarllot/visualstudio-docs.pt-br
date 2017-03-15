---
title: Tarefa XmlPeek | Microsoft Docs
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
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
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
ms.openlocfilehash: 91ebdc892225426e6f04272c7e667197cc39d395
ms.lasthandoff: 02/22/2017

---
# <a name="xmlpeek-task"></a>Tarefa XmlPeek
Retorna os valores conforme especificado por uma consulta de XPath em um arquivo XML.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `XmlPeek`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Namespaces`|Parâmetro `String` opcional.<br /><br /> Especifica os namespaces para prefixos de consulta do XPath.|  
|`Query`|Parâmetro `String` opcional.<br /><br /> Especifica a consulta do XPath.|  
|`Result`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os resultados que são retornados por essa tarefa.|  
|`XmlContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XML como uma cadeia de caracteres.|  
|`XmlInputPath`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica a entrada XML como um caminho de arquivo.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
