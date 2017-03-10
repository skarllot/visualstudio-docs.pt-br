---
title: "Elemento Output (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Elemento <Output> [MSBuild]"
  - "Elemento Output [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Output (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Valores de saída da tarefa de armazenamentos em itens e propriedades.  
  
## Sintaxe  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`TaskParameter`|Atributo obrigatório.<br /><br /> O nome da tarefa do parâmetro de saída.|  
|`PropertyName`|Tanto o `PropertyName` ou `ItemName` o atributo é necessário.<br /><br /> A propriedade que recebe a tarefa de saída do valor do parâmetro.  Seu projeto pode fazer referência a propriedade com o `$(`*PropertyName*`)` sintaxe.  Este nome de propriedade pode ser um novo nome de propriedade ou um nome que já está definido no projeto.<br /><br /> Esse atributo não pode ser usado se `ItemName` também está sendo usado.|  
|`ItemName`|Tanto o `PropertyName` ou `ItemName` o atributo é necessário.<br /><br /> O valor do parâmetro de saída do item que recebe a tarefa.  Seu projeto pode fazer referência o item com o `@(`*ItemName*`)` sintaxe.  O nome do item pode ser um novo nome de item ou um nome que já está definido no projeto.<br /><br /> Esse atributo não pode ser usado se `PropertyName` também está sendo usado.|  
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### Elementos filho  
 Nenhum.  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Tarefa](../msbuild/task-element-msbuild.md)|Cria e executa uma instância de um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarefa.|  
  
## Exemplo  
 O seguinte código exemplo mostra a `Csc` tarefa sendo executada dentro de um `Target` elemento.  Os itens e propriedades passadas para os parâmetros da tarefa são declaradas fora do escopo desse exemplo.  O valor do parâmetro de saída `OutputAssembly` é armazenado na `FinalAssemblyName` item e o valor do parâmetro de saída `BuildSucceeded` é armazenado na `BuildWorked` propriedade.  Para obter mais informações, consulte [ \(tarefas\)](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)