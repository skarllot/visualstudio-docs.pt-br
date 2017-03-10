---
title: "Tarefa GetFrameworkSdkPath | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa GetFrameworkSdkPath [MSBuild]"
  - "MSBuild, Tarefa GetFrameworkSdkPath"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GetFrameworkSdkPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera o caminho para o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `GetFrameworkSdkPath` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`FrameworkSdkVersion20Path`|Opcional `String` parâmetro de saída somente leitura.<br /><br /> Retorna o caminho para o.NET SDK versão 2.0, se presente.  Caso contrário, retornará `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Opcional `String` parâmetro de saída somente leitura.<br /><br /> Retorna o caminho para o.NET SDK versão 3.5, se presente.  Caso contrário, retornará `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Opcional `String` parâmetro de saída somente leitura.<br /><br /> Retorna o caminho para o.NET SDK versão 4.0, se presente.  Caso contrário, retornará `String.Empty`.|  
|`Path`|Opcional `String` parâmetro de saída.<br /><br /> Contém o caminho para o mais recente.NET SDK, se qualquer versão estiver presente.  Caso contrário, retornará `String.Empty`.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a `GetFrameworkSdkPath` tarefas para armazenar o caminho para o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] na `SdkPath` propriedade.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)