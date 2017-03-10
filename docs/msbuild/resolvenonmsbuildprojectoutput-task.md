---
title: "Tarefa ResolveNonMSBuildProjectOutput | Microsoft Docs"
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
  - "MSBuild, Tarefa ResolveNonMSBuildProjectOutput"
  - "Tarefa ResolveNonMSBuildProjectOutput [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa ResolveNonMSBuildProjectOutput
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina os arquivos de saída não\-MSBuild referências do projeto.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `ResolveNonMSBuildProjectOutput` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`PreresolvedProjectOutputs`|Opcional `String` parâmetro.<br /><br /> Especifica uma cadeia XML que contém resolvido saídas de projeto.|  
|`ProjectReferences`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica as referências do projeto.|  
|`ResolvedOutputPaths`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém a lista de caminhos de referência resolvido \(e preserva os atributos de referência do projeto original\).|  
|`UnresolvedProjectReferences`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém a lista de itens de referência de projeto que não puderam ser resolvidos usando a lista preresolved de saídas.<br /><br /> Porque somente o Visual Studio preresolves não\-MSBuild projetos, isso significa que as referências de projeto nesta lista estão no formato do MSBuild.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)