---
title: "Tarefa AssignCulture | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa AssignCulture [MSBuild]"
  - "MSBuild, Tarefa AssignCulture"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa AssignCulture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta tarefa aceita uma lista de itens que podem conter um válido.String de identificador de cultura NET como parte do nome do arquivo e produz itens que possuem um metadados chamado `Culture` identificador de cultura que contém o correspondente.  Por exemplo, o nome do arquivo Form1.fr\-FR tem uma cultura incorporada identificador "fr\-fr", para que essa tarefa produzirá um item que tem o mesmo nome de arquivo com os metadados `Culture` igual a `fr-fr`.  A tarefa também produz uma lista de nomes de arquivos com a cultura removida do nome de arquivo.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `AssignCulture` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AssignedFiles`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém a lista de itens recebidos na `Files` parâmetro, com um `Culture` a entrada de metadados adicionada para cada item.<br /><br /> Se a entrada do item da `Files` parâmetro já contém um `Culture` entrada de metadados, a entrada de metadados original será usada.<br /><br /> A tarefa apenas atribui uma `Culture` a entrada de metadados se o nome do arquivo contém um identificador de cultura válida.  O identificador de cultura deve ser entre os dois últimos pontos no nome do arquivo.|  
|`AssignedFilesWithCulture`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém o subconjunto de itens da `AssignedFiles` parâmetro que possuem um `Culture` a entrada de metadados.|  
|`AssignedFilesWithNoCulture`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém o subconjunto de itens da `AssignedFiles` parâmetro que não possuem um `Culture` a entrada de metadados.|  
|`CultureNeutralAssignedFiles`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém a mesma lista de itens que é produzido na `AssignedFiles` parâmetro, exceto com a cultura removida do nome do arquivo.<br /><br /> A tarefa remove apenas a cultura do nome do arquivo se ele é um identificador de cultura válida.|  
|`Files`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica a lista de arquivos com nomes de cultura incorporadas para atribuir uma cultura para.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir executa a `AssignCulture` de tarefas com o `ResourceFiles` item da coleção.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 A tabela a seguir descreve o valor dos itens de saída após a execução da tarefa.  Os metadados de item é mostrado entre parênteses após o item.  
  
|Coleção de item|Contents|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx`\(não há metadados adicionais\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx`\(não há metadados adicionais\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`Não há metadados adicionais\)|  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)