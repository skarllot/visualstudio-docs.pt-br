---
title: "Tarefa FindInList | Microsoft Docs"
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
  - "Tarefa FindInList [MSBuild]"
  - "MSBuild, Tarefa FindInList"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa FindInList
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em uma lista especificada, localiza um item que tem o itemspec correspondente.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da [FindInList Task](../msbuild/findinlist-task.md).  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`CaseSensitive`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, a pesquisa é diferencia maiúsculas de minúsculas; Caso contrário, ele não é.  Valor padrão é `true`.|  
|`FindLastMatch`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, retornar a última correspondência; Caso contrário, retornará a primeira correspondência.  Valor padrão é `false`.|  
|`ItemFound`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída somente leitura.<br /><br /> Item a primeira correspondência encontrada na lista, se houver.|  
|`ItemSpecToFind`|Obrigatório `String` parâmetro.<br /><br /> Para procurar a itemspec.|  
|`List`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> A lista na qual procurar a itemspec.|  
|`MatchFileNameOnly`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, correspondência com apenas a parte de nome de arquivo da itemspec; Caso contrário, correspondência com a itemspec inteiro.  Valor padrão é `true`.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)