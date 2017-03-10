---
title: "Tarefa CallTarget | Microsoft Docs"
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
  - "Tarefa CallTarget [MSBuild]"
  - "MSBuild, Tarefa CallTarget"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa CallTarget
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Chama os destinos especificados no arquivo de projeto.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `CallTarget` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`RunEachTargetSeparately`|Opcional `Boolean` parâmetro de saída.<br /><br /> Se `true`, o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] engine é chamado uma vez por destino.  Se `false`, o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] engine é chamado uma vez para todos os destinos de compilação.  O valor padrão é `false`.|  
|`TargetOutputs`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém as saídas de todos os destinos de compilação.|  
|`Targets`|Opcional `String[]` parâmetro.<br /><br /> Especifica o destino ou destinos de compilação.|  
|`UseResultsCache`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, o resultado em cache é retornado se estiver presente.<br /><br /> **Nota**  quando MSBuild uma tarefa é executada, sua saída é armazenada em cache em um escopo \(ProjectFileName, GlobalProperties\) \[TargetNames\] como uma lista de itens de compilação.|  
  
## Comentários  
 Se um destino especificado em `Targets` falhar e `RunEachTargetSeparately` é `true`, a tarefa continuará a criar os destinos restantes.  
  
 Se você quiser construir os destinos padrão, use o [Tarefa MSBuild](../msbuild/msbuild-task.md) e defina a `Projects` parâmetro igual a `$(MSBuildProjectFile)`.  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir chama `TargetA` de dentro de `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)