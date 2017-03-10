---
title: "Tarefa ConvertToAbsolutePath | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa ConvertToAbsolutePath [MSBuild]"
  - "MSBuild, Tarefa ConvertToAbsolutePath"
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa ConvertToAbsolutePath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Converte um caminho relativo, ou referência, em um caminho absoluto.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `ConvertToAbsolutePath` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Paths`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> A lista de caminhos relativos para converter em caminhos absolutos.|  
|`AbsolutePaths`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> A lista de caminhos absolutos para os itens que foram passados.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)