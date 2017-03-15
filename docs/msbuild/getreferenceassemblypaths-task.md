---
title: Tarefa GetReferenceAssemblyPaths | Microsoft Docs
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
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
ms.openlocfilehash: 95757ad06e23165021a02e0397f4b8cb7926d476
ms.lasthandoff: 02/22/2017

---
# <a name="getreferenceassemblypaths-task"></a>Tarefa GetReferenceAssemblyPaths
Retorna os caminhos do assembly de referência de diversas estruturas.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `GetReferenceAssemblyPaths`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parâmetro de saída `String[]` opcional.<br /><br /> Retorna o caminho com base no parâmetro `TargetFrameworkMoniker`. Se o `TargetFrameworkMoniker` for nulo ou vazio, esse caminho será `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parâmetro de saída `String[]` opcional.<br /><br /> Retorna o caminho com base no parâmetro `TargetFrameworkMoniker`, sem considerar a parte do perfil do moniker. Se o `TargetFrameworkMoniker` for nulo ou vazio, esse caminho será `String.Empty`.|  
|`TargetFrameworkMoniker`|Parâmetro `String` opcional.<br /><br /> Especifica o moniker da estrutura de destino associada aos caminhos de assembly de referência.|  
|`RootPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho raiz a ser usado para gerar o caminho do assembly de referência.|  
|`BypassFrameworkInstallChecks`|Parâmetro [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) opcional.<br /><br /> Se `true`, ignora as verificações básicas que `GetReferenceAssemblyPaths` executa por padrão para garantir que determinadas estruturas de tempo de execução sejam instaladas, dependendo da estrutura de destino.|  
|`TargetFrameworkMonikerDisplayName`|Parâmetro de saída `String` opcional.<br /><br /> Especifica o nome de exibição do moniker da estrutura de destino.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
