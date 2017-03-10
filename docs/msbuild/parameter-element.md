---
title: "Elemento Parameter (MSBuild) | Microsoft Docs"
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
  - "Elemento <Parameter> [MSBuild]"
  - "elemento Parameter [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Parameter (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contém informações sobre um parâmetro específico para uma tarefa que é gerado por um `UsingTask``TaskFactory`.  O nome do elemento é o nome do parâmetro.  Para obter mais informações, consulte [Elemento UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Sintaxe  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`ParameterType`|Atributo opcional.<br /><br /> A.NET tipo do parâmetro, por exemplo, "System. String".|  
|`Output`|Atributo booleano opcional.<br /><br /> Se `true`, este parâmetro é um parâmetro de saída para a tarefa.  Por padrão, o valor é `false`.|  
|`Required`|Atributo booleano opcional.<br /><br /> Se `true`, este parâmetro é um parâmetro obrigatório para a tarefa.  Por padrão, o valor é `false`.|  
  
### Elementos filho  
 Nenhum.  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contém uma lista opcional de parâmetros que estarão presentes na tarefa que é gerada por um `UsingTask``TaskFactory`.|  
  
## Exemplo  
 O exemplo a seguir mostra como usar o `Parameter` elemento.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)