---
title: "Tarefa GetFrameworkPath | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa GetFrameworkPath [MSBuild]"
  - "MSBuild, Tarefa GetFrameworkPath"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GetFrameworkPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera o caminho para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assemblies.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `GetFrameworkPath` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`FrameworkVersion11Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para os assemblies do framework versão 1.1, se presente.  Caso contrário, retornará `null`.|  
|`FrameworkVersion20Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para os assemblies do framework versão 2.0, se presente.  Caso contrário, retornará `null`.|  
|`FrameworkVersion30Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para os assemblies do framework versão 3.0, se presente.  Caso contrário, retornará `null`.|  
|`FrameworkVersion35Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para os assemblies do framework versão 3.5, se presente.  Caso contrário, retornará `null`.|  
|`FrameworkVersion40Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para os assemblies do framework versão 4.0, se presente.  Caso contrário, retornará `null`.|  
|`Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para os assemblies do framework mais recentes, se houver alguma disponíveis.  Caso contrário, retornará `null`.|  
  
## Comentários  
 Se várias versões da [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] são instalados, essa tarefa retorna a versão que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] foi projetado para ser executado no.  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a `GetFrameworkPath` tarefas para armazenar o caminho para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] na `FrameworkPath` propriedade.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)