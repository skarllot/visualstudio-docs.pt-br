---
title: "Tarefa MakeDir | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#MakeDir"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa MakeDir [MSBuild]"
  - "MSBuild, Tarefa MakeDir"
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa MakeDir
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cria diretórios e, se necessário, qualquer pai diretórios.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `MakeDir` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Directories`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> O conjunto de diretórios para criar.|  
|`DirectoriesCreated`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Os diretórios que são criados por essa tarefa.  Se alguns diretórios não podem ser criados, isso pode não conter todos os itens que foram passados para o `Directories` parâmetro.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O seguinte exemplo de código usa a `MakeDir` tarefa para criar o diretório especificado pela `OutputDirectory` propriedade.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)