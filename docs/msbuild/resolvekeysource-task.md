---
title: Tarefa ResolveKeySource | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
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
ms.openlocfilehash: 32d9019c8eeeef7ced9ef54d751fdc1de509ba62
ms.lasthandoff: 02/22/2017

---
# <a name="resolvekeysource-task"></a>Tarefa ResolveKeySource
Determina a origem da chave de nome forte.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `ResolveKeySource`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Parâmetro `Int32` opcional.<br /><br /> Obtém ou define a quantidade de tempo, em segundos, para exibir a contagem de mensagem de inatividade.|  
|`AutoClosePasswordPromptTimeout`|Parâmetro `Int32` opcional.<br /><br /> Obtém ou define o período de tempo, em segundos, a esperar antes de fechar a caixa de diálogo de aviso de senha.|  
|`CertificateFile`|Parâmetro `String` opcional.<br /><br /> Obtém ou define o caminho do arquivo do certificado.|  
|`CertificateThumbprint`|Parâmetro `String` opcional.<br /><br /> Obtém ou define a impressão digital do certificado.|  
|`KeyFile`|Parâmetro `String` opcional.<br /><br /> Obtém ou define o caminho do arquivo da chave.|  
|`ResolvedKeyContainer`|Parâmetro de saída `String` opcional.<br /><br /> Obtém ou define o contêiner de chave resolvido.|  
|`ResolvedKeyFile`|Parâmetro de saída `String` opcional.<br /><br /> Obtém ou define o contêiner de arquivo resolvido.|  
|`ResolvedThumbprint`|Parâmetro de saída `String` opcional.<br /><br /> Obtém ou define a impressão digital do certificado resolvido.|  
|`ShowImportDialogDespitePreviousFailures`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, mostra a caixa de diálogo Importar apesar das falhas anteriores.|  
|`SuppressAutoClosePasswordPrompt`|Parâmetro `Boolean` opcional.<br /><br /> Obtém ou define um valor booliano que especifica se a caixa de diálogo de aviso de senha deve não fechamento automático.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
