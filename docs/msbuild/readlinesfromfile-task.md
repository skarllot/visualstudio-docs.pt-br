---
title: "Tarefa ReadLinesFromFile | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa ReadLinesFromFile"
  - "Tarefa ReadLinesFromFile [MSBuild]"
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa ReadLinesFromFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lê uma lista de itens de um arquivo de texto.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros do `ReadLinesFromFile` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`File`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o arquivo para leitura.  O arquivo deve ter um item em cada linha.|  
|`Lines`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém as linhas ler do arquivo.|  
  
## Comentários  
 Além para os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> classe, que herda de <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa o `ReadLinesFromFile` tarefa para criar itens de uma lista em um arquivo de texto.  Os itens ler do arquivo são armazenados no `ItemsFromFile` item da coleção.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
    </ItemGroup>  
  
    <Target Name="ReadFromFile">  
        <ReadLinesFromFile  
            File="@(MyTextFile)" >  
            <Output  
                TaskParameter="Lines"  
                ItemName="ItemsFromFile"/>  
        </ReadLinesFromFile>  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)