---
title: "Tarefa ResolveKeySource | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa ResolveKeySource"
  - "Tarefa ResolveKeySource [MSBuild]"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa ResolveKeySource
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina a fonte de chave de nome forte.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `ResolveKeySource` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AutoClosePasswordPromptShow`|Opcional `Int32` parâmetro.<br /><br /> Obtém ou define a quantidade de tempo, em segundos, para exibir a contagem regressiva de mensagem.|  
|`AutoClosePasswordPromptTimeout`|Opcional `Int32` parâmetro.<br /><br /> Obtém ou define a quantidade de tempo, em segundos, para aguardar antes de fechar a caixa de diálogo de aviso de senha.|  
|`CertificateFile`|Opcional `String` parâmetro.<br /><br /> Obtém ou define o caminho do arquivo de certificado.|  
|`CertificateThumbprint`|Opcional `String` parâmetro.<br /><br /> Obtém ou define a impressão digital do certificado.|  
|`KeyFile`|Opcional `String` parâmetro.<br /><br /> Obtém ou define o caminho do arquivo de chave.|  
|`ResolvedKeyContainer`|Opcional `String` parâmetro de saída.<br /><br /> Obtém ou define o recipiente de chave resolvido.|  
|`ResolvedKeyFile`|Opcional `String` parâmetro de saída.<br /><br /> Obtém ou define o arquivo de chave resolvido.|  
|`ResolvedThumbprint`|Opcional `String` parâmetro de saída.<br /><br /> Obtém ou define a impressão digital do certificado resolvido.|  
|`ShowImportDialogDespitePreviousFailures`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, mostrar a caixa de diálogo Importar apesar das falhas anteriores.|  
|`SuppressAutoClosePasswordPrompt`|Opcional `Boolean` parâmetro.<br /><br /> Obtém ou define um valor booleano que especifica se a caixa de diálogo de aviso de senha deve sem fechamento automático.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)