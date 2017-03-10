---
title: "Tarefa VCMessage | Microsoft Docs"
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
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tarefa VCMessage"
  - "tarefa VCMessage (MSBuild (Visual C++))"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa VCMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aviso de logs e mensagens de erro durante uma compilação.  
  
## Comentários  
 Esta tarefa ajuda a implementar o MSBuild para Visual C\+\+ e não se destina a ser chamado pelo usuário.  Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da **VCMessage** tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**Arguments**|Opcional **String** parâmetro.<br /><br /> Uma lista delimitada por ponto e de mensagens a serem exibidas.|  
|**Code**|Obrigatório **String** parâmetro.<br /><br /> Um número de erro que qualifica a mensagem.|  
|**Type**|Opcional **String** parâmetro.<br /><br /> Especifica o tipo de mensagem para emitir.  Especificar o  `"Aviso"` emitir uma mensagem de aviso, ou  `"Erro"` emitir uma mensagem de erro.|  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)