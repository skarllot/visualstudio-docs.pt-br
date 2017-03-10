---
title: "Tarefa RemoveDuplicates | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa RemoveDuplicates"
  - "Tarefa RemoveDuplicates [MSBuild]"
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa RemoveDuplicates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Remove duplica itens da coleção especificada.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros do `RemoveDuplicates` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Filtered`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém uma coleção de item com itens duplicados todos removidos.|  
|`Inputs`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> A coleção de item para remover itens duplicados.|  
  
## Comentários  
 Esta tarefa diferencia maiúsculas de minúsculas e não compara os metadados de item ao determinar duplicatas.  
  
 Além para os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> classe, que herda de <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa o `RemoveDuplicates` tarefa para remover itens duplicados do `MyItems` item da coleção.  Quando a tarefa estiver concluída, o `FilteredItems` item coleção contém um item.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)