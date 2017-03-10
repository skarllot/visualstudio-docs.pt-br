---
title: "Tarefa SetEnv | Microsoft Docs"
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
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tarefas"
  - "Tarefa SetEnv (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa SetEnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define ou exclui o valor de uma variável de ambiente especificada.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da **SetEnv** tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**Name**|Obrigatório **String** parâmetro.<br /><br /> O nome de uma variável de ambiente.|  
|**OutputEnvironmentVariable**|Opcional **String** parâmetro de saída.<br /><br /> Contém o valor atribuído à variável de ambiente especificado pelo **Name** parâmetro.|  
|**Prefix**|Obrigatório `Boolean` parâmetro.<br /><br /> Se `true`, concatena o valor da **Value** parâmetro antes do valor da variável de ambiente especificado pelo **Name** parâmetro e, em seguida, atribui o resultado à variável de ambiente.  Se `false`, atribui apenas o valor da **Value** parâmetro para a variável de ambiente.|  
|**Target**|Opcional **String** parâmetro.<br /><br /> Especifica o local onde uma variável de ambiente é armazenada.  Especificar "`usuário`"ou"`máquina`".<br /><br /> Para obter mais informações, consulte "EnvironmentVariableTarget Enumeration" sobre o [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**Value**|Opcional **String** parâmetro.<br /><br /> O valor atribuído à variável de ambiente especificado pelo **Name** parâmetro.  Se **Value** está vazio e a variável existe, a variável será excluída.  Se a variável não existir, nenhum erro ocorre mesmo que a operação não pode ser executada.<br /><br /> Para obter mais informações, consulte o "Método de Environment::SetEnvironmentVariable" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
  
## Comentários  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)