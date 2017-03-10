---
title: Tarefa XslTransformation | Microsoft Docs
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
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
ms.openlocfilehash: d240cca44bf389f97eaa7f4709690c0dc89cacc1
ms.lasthandoff: 02/22/2017

---
# <a name="xsltransformation-task"></a>Tarefa XslTransformation
Transformações um XML de entrada usando um XSLT ou XSLT compilado e saídas para um arquivo ou um dispositivo de saída.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `XslTransformation`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`OutputPaths`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos de saída para a transformação XML.|  
|`Parameters`|Parâmetro `String` opcional.<br /><br /> Especifica os parâmetros para o documento de entrada XSLT.|  
|`XmlContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XML como uma cadeia de caracteres.|  
|`XmlInputPaths`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos de entrada XML.|  
|`XslCompiledDllPath`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o XSLT compilado.|  
|`XslContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XSLT como uma cadeia de caracteres.|  
|`XslInputPath`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o arquivo de entrada XSLT.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
