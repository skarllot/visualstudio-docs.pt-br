---
title: "Tarefa XmlPoke | Microsoft Docs"
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
  - "MSBuild, Tarefa XmlPoke"
  - "Tarefa XmlPoke [MSBuild]"
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa XmlPoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define os valores conforme especificado por uma consulta XPath em um arquivo XML.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `XmlPoke` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Namespaces`|Opcional `String` parâmetro.<br /><br /> Especifica os namespaces para prefixos de consulta XPath.|  
|`Query`|Opcional `String` parâmetro.<br /><br /> Especifica a consulta XPath.|  
|`Value`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o arquivo de saída.|  
|`XmlInputPath`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica a entrada XML como um caminho de arquivo.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)