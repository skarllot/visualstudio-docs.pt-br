---
title: "Elemento Task (MSBuild) | Microsoft Docs"
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
  - "Elemento <Task> [MSBuild]"
  - "elemento Task [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Task (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

cria e executa uma instância de uma tarefa de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .  O nome do elemento é determinado pelo nome da tarefa que está sendo criada.  
  
## Sintaxe  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem elementos filho, atributos, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Condition`|atributo opcional.  Condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|atributo opcional.  Pode conter um dos seguintes valores:<br /><br /> -   **WarnAndContinue** ou **true**.  Quando uma tarefa falhar, as tarefas subseqüentes no elemento de [Destino](../msbuild/target-element-msbuild.md) na compilação e continuar a executar, e todos os erros de tarefa são tratados como avisos.<br />-   **ErrorAndContinue**.  Quando uma tarefa falhar, as tarefas subseqüentes no elemento de `Target` na compilação e continuar a executar, e todos os erros de tarefa são tratados como erros.<br />-   **ErrorAndStop** ou **false** \(padrão\).  Quando uma tarefa falhar, as outras tarefas no elemento de `Target` e na compilação não são executadas, e o elemento inteiro de `Target` e a construção são considerados ter falhado.<br /><br /> As versões do .NET Framework 4,5 antes de suportavam apenas os valores de `true` e de `false` .<br /><br /> Para obter mais informações, consulte [Como ignorar erros em tarefas](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md).|  
|`Parameter`|Necessário se a classe de tarefa contém uma ou mais propriedades rotuladas com o atributo de `[Required]` .<br /><br /> Um parâmetro definido pelo usuário na tarefa que contém o valor do parâmetro como seu valor.  Pode haver qualquer número de parâmetros no elemento de `Task` , com cada atributo que mapeia a uma propriedade .NET na classe de tarefas.|  
  
### Elementos filho  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Saída](../msbuild/output-element-msbuild.md)|Armazena a saída de tarefa no arquivo de projeto.  pode haver zero ou mais elementos de `Output` em uma tarefa.|  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Destino](../msbuild/target-element-msbuild.md)|Elemento contêiner para tarefas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  
  
## Comentários  
 Um elemento de `Task` em um arquivo de projeto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] cria uma instância de uma tarefa, define propriedades em ele, e as executa em.  Parâmetros de saída dos armazenamentos do elemento de `Output` nas propriedades ou nos itens a serem usadas em qualquer lugar no arquivo de projeto.  
  
 Se houver qualquer elemento de [OnError](../msbuild/onerror-element-msbuild.md) no elemento pai de `Target` de uma tarefa, serão avaliados ainda se a tarefa falha e `ContinueOnError` tem um valor de `false`.  Para obter mais informações sobre as tarefas, consulte [ \(tarefas\)](../msbuild/msbuild-tasks.md).  
  
## Exemplo  
 O exemplo de código a seguir cria uma instância da classe de [Tarefa de CSC](../msbuild/csc-task.md) , define seis propriedades, e executar a tarefa.  Após a execução, o valor da propriedade de `OutputAssembly` de objeto é colocado em uma lista de itens `FinalAssemblyName`chamada.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)