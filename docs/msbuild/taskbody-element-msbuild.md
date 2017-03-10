---
title: "Elemento TaskBody (MSBuild) | Microsoft Docs"
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
  - "Elemento <TaskBody> [MSBuild]"
  - "Elemento TaskBody [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento TaskBody (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contém os dados que são passados para um `UsingTask``TaskFactory`. Para obter mais informações, consulte [Elemento UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Sintaxe  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Evaluate`|Atributo booleano opcional.<br /><br /> Se `true`, MSBuild avalia quaisquer elementos internos e expande os itens e propriedades antes de transmitir as informações para o `TaskFactory` quando a tarefa é instanciada.|  
  
### Elementos filho  
  
|Elemento|Descrição|  
|--------------|---------------|  
|Dados|O texto entre o `TaskBody` marcas é enviada literalmente para o `TaskFactory`.|  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Fornece uma maneira de registrar tarefas em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Pode haver zero ou mais `UsingTask` elementos em um projeto.|  
  
## Exemplo  
 O exemplo a seguir mostra como usar o `TaskBody` elemento com um `Evaluate` atributo.  
  
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