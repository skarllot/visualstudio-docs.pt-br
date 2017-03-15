---
title: Tarefa de mensagem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 23
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: e2c4a65b44ea3cdc9ed54911e8037467e5ce5554
ms.lasthandoff: 02/22/2017

---
# <a name="message-task"></a>Tarefa Message
Registra uma mensagem durante a compilação.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Message`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Importance`|Parâmetro `String` opcional.<br /><br /> Especifica a importância da mensagem. Esse parâmetro pode ter um valor igual a `high`, `normal` ou `low`. O valor padrão é `normal`.|  
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto de erro do log.|  
  
## <a name="remarks"></a>Comentários  
 A tarefa `Message` permite o envio de mensagens de problema para os agentes de log em diferentes etapas no processo de compilação de projetos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Se o parâmetro `Condition` avaliar para o `true`, o valor do parâmetro `Text` será registrado e a compilação dará continuidade à execução. Se um parâmetro `Condition` não existir, o texto da mensagem será registrado. Para obter mais informações sobre registro, consulte [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Por padrão, a mensagem é enviada para o agente de log de console do MSBuild. Isso pode ser alterado definindo o parâmetro <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. O agente de log interpreta o parâmetro `Importance`.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir registra mensagens para todos os agentes de log registrados.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Obtendo Logs de Build](../msbuild/obtaining-build-logs-with-msbuild.md)
