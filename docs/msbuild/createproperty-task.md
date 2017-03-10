---
title: "Tarefa CreateProperty | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa CreateProperty [MSBuild]"
  - "MSBuild, Tarefa CreateProperty"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa CreateProperty
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Preenche as propriedades com os valores passados.  Isso permite que os valores a serem copiados de uma propriedade ou seqüência de caracteres para outro.  
  
## Atributos  
 A tabela a seguir descreve os parâmetros da `CreateProperty` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Value`|Opcional `String` parâmetro de saída.<br /><br /> Especifica o valor para copiar para a nova propriedade.|  
|`ValueSetByTask`|Opcional `String` parâmetro de saída.<br /><br /> Contém o mesmo valor que o `Value` parâmetro.  Use este parâmetro somente quando desejar evitar ter a propriedade de saída definida por [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] quando ela ignora o delimitador de destino porque as saídas estão atualizadas.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a `CreateProperty` tarefa para criar o `NewFile` propriedade usando a combinação dos valores da `SourceFilename` e `SourceFileExtension` propriedade.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Após a execução do projeto, o valor da `NewFile` propriedade é `Module1.vb`.  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)