---
title: "Tarefa AssignTargetPath | Microsoft Docs"
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa AssignTargetPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa tarefa aceita arquivos de lista e adiciona atributos `<TargetPath>` se ainda não foram especificados.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `AssignTargetPath`.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`RootFolder`|Parâmetro de entrada `string` opcional.<br /><br /> Contém o caminho para a pasta que contém os links de destino.|  
|`Files`|Parâmetro de entrada opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Contém a lista de entrada de arquivos.|  
|`AssignedFiles`|Opcional<br /><br /> Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Contém a lista de resultados de arquivos.|  
  
## Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que é herdada da própria classe <xref:Microsoft.Build.Utilities.Task>.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir executa a tarefa `AssignTargetPath` para configurar um projeto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)