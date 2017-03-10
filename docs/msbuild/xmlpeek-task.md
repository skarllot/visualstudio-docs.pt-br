---
title: "Tarefa XmlPeek | Microsoft Docs"
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
  - "MSBuild, Tarefa XmlPeek"
  - "Tarefa XmlPeek [MSBuild]"
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa XmlPeek
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Retorna os valores conforme especificado pela consulta XPath de um arquivo XML.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `XmlPeek` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Namespaces`|Opcional `String` parâmetro.<br /><br /> Especifica os namespaces para os prefixos de consulta XPath.|  
|`Query`|Opcional `String` parâmetro.<br /><br /> Especifica a consulta XPath.|  
|`Result`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém os resultados retornados por essa tarefa.|  
|`XmlContent`|Opcional `String` parâmetro.<br /><br /> Especifica a entrada XML como uma seqüência de caracteres.|  
|`XmlInputPath`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica a entrada XML como um caminho de arquivo.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)