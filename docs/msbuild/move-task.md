---
title: "Tarefa Move | Microsoft Docs"
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
  - "tarefa Move [MSBuild]"
  - "MSBuild, tarefa Move"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa Move
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Move os arquivos para um novo local.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `Move` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`DestinationFiles`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Especifica a lista de arquivos para mover os arquivos de origem.  Essa lista deve ser um mapeamento individual à lista que é especificado na `SourceFiles` parâmetro.  Ou seja, o primeiro arquivo especificado em `SourceFiles` serão movidos para o primeiro local especificado em `DestinationFiles`, e assim por diante.|  
|`DestinationFolder`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o diretório ao qual você deseja mover os arquivos.|  
|`MovedFiles`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém os itens que foram movidos com êxito.|  
|`OverwriteReadOnlyFiles`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, substitui arquivos mesmo se eles estiverem marcados como arquivos somente leitura.|  
|`SourceFiles`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os arquivos para mover.|  
  
## Comentários  
 Tanto o `DestinationFolder` parâmetro ou o `DestinationFiles` parâmetro deve ser especificado, mas não ambos.  Se ambos forem especificados, a tarefa falha e um erro será registrado.  
  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)