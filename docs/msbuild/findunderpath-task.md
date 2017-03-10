---
title: "Tarefa FindUnderPath | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa FindUnderPath [MSBuild]"
  - "MSBuild, Tarefa FindUnderPath"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa FindUnderPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina quais itens na coleção item especificado têm caminhos que estão em ou abaixo da pasta especificada.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros do `FindUnderPath` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Files`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os arquivos cujos caminhos devem ser comparados com o caminho especificado pelo `Path` parâmetro.|  
|`InPath`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém os itens que foram encontrados no caminho especificado.|  
|`OutOfPath`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém os itens que não foram encontrados no caminho especificado.|  
|`Path`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o caminho de pasta para usar como referência.|  
|`UpdateToAbsolutePaths`|Opcional `Boolean` parâmetro.<br /><br /> Se verdadeiro, os caminhos dos itens de saída são atualizados para ser caminhos absolutos.|  
  
## Comentários  
 Além para os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> classe, que herda de <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa o `FindUnderPath` tarefas para determinar se os arquivos continham na `MyFiles` item têm caminhos que existe no caminho especificado pelo `SearchPath` propriedade.  Após a conclusão da tarefa, o `FilesNotFoundInPath` item contém o `File1.txt` arquivo e o `FilesFoundInPath` item contém o `File2.txt` arquivo.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)