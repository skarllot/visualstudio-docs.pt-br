---
title: Tarefa AssignProjectConfiguration | Microsoft Docs
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
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 7
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
ms.openlocfilehash: 80fe9e734dd8af527fad318df17f9c456129d660

---
# <a name="assignprojectconfiguration-task"></a>Tarefa AssignProjectConfiguration
Essa tarefa aceita cadeias de caracteres de configuração de lista e as atribui a projetos especificados.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `AssignProjectConfiguration`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Parâmetro de saída `string` opcional.<br /><br /> Contém uma cadeia de caracteres XML com uma configuração de projeto para cada projeto. As configurações são atribuídas aos projetos nomeados.|  
|`DefaultToVcxPlatformMapping`|Parâmetro de saída `string` opcional.<br /><br /> Contém uma lista delimitada por ponto e vírgula de mapeamentos dos nomes de plataforma usados<br /><br /> pela maioria dos tipos para aqueles usadas pelos arquivos .vcxproj.<br /><br /> Por exemplo:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Opcional<br /><br /> Parâmetro de saída `string`.<br /><br /> Contém uma lista delimitada por ponto-e-vírgula de mapeamentos de nomes de plataforma .vcxproj para os nomes de plataforma usados pela maioria dos tipos.<br /><br /> Por exemplo:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Parâmetro de saída `string` opcional.<br /><br /> Contém a configuração para o projeto atual.|  
|`CurrentProjectPlatform`|Parâmetro de saída `string` opcional.<br /><br /> Contém a plataforma para o projeto atual.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Parâmetro de saída `bool` opcional.<br /><br /> Contém um sinalizador que indica que referências devem ser criadas mesmo que tenham sido desabilitadas na configuração do projeto.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Parâmetro de saída `bool` opcional.<br /><br /> Contém um sinalizador que indica se a configuração pai e a plataforma devem ser desfeitas.|  
|`OutputType`|Parâmetro de saída `string` opcional.<br /><br /> Contém o tipo de saída para o projeto.|  
|`ResolveConfigurationPlatformUsingMappings`|Parâmetro de saída `bool` opcional.<br /><br /> Contém um sinalizador que indica se o build deve usar os mapeamentos padrão para resolver a configuração e a plataforma do aprovado nas referências do projeto.|  
|`AssignedProjects`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de caminhos de referência resolvidos.|  
|`UnassignedProjects`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de itens de referência de projeto que não puderam ser resolvidos usando a lista de saídas pré-resolvida.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)


<!--HONumber=Feb17_HO4-->


