---
title: "Tarefa FindAppConfigFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa FindAppConfigFile [MSBuild]"
  - "MSBuild, Tarefa FindAppConfigFile"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa FindAppConfigFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Localiza o arquivo app. config, se houver, nas listas fornecidas.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `FindAppConfigFile` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AppConfigFile`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Especifica o primeiro item coincidente encontrado na lista, se houver.|  
|`PrimaryList`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica a lista principal para pesquisar.|  
|`SecondaryList`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica a lista secundária para pesquisar.|  
|`TargetPath`|Obrigatório `String` parâmetro.<br /><br /> Especifica o valor para adicionar como metadados.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)