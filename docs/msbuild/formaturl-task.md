---
title: "Tarefa FormatUrl | Microsoft Docs"
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
  - "Tarefa FormatUrl [MSBuild]"
  - "MSBuild, Tarefa FormatUrl"
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa FormatUrl
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Converte uma URL em um formato de URL correto.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `FormatUrl` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`InputUrl`|Opcional `String` parâmetro.<br /><br /> Especifica a URL para formatar.|  
|`OutputUrl`|Opcional `String` parâmetro de saída.<br /><br /> Especifica a URL formatada.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)