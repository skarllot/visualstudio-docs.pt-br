---
title: "Elemento UsingTask (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Elemento <UsingTask> [MSBuild]"
  - "Elemento UsingTask [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento UsingTask (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mapeia a tarefa que é referenciada em uma [tarefas](../msbuild/task-element-msbuild.md) elemento para o assembly que contém a implementação de tarefas.  
  
## Sintaxe  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`AssemblyName`|Tanto o `AssemblyName` atributo ou o `AssemblyFile` atributo é necessário.<br /><br /> O nome do assembly a ser carregado.  O `AssemblyName` atributo aceita os assemblies de nome forte, embora não seja necessário com nomes fortes.  Usar esse atributo equivale ao carregar um assembly usando o <xref:System.Reflection.Assembly.Load%2A> método no .NET.<br /><br /> Você não pode usar esse atributo, se o `AssemblyFile` atributo será usado.|  
|`AssemblyFile`|Tanto o `AssemblyName` ou o `AssemblyFile` atributo é necessário.<br /><br /> O caminho do arquivo do assembly.  Esse atributo aceita caminhos completos ou caminhos relativos.  Caminhos relativos são relativos ao diretório do arquivo de projeto ou arquivo de destinos onde o `UsingTask` elemento é declarado.  Usar esse atributo equivale ao carregar um assembly usando o <xref:System.Reflection.Assembly.LoadFrom%2A> método no .NET.<br /><br /> Você não pode usar esse atributo, se o `AssemblyName` atributo será usado.|  
|`TaskFactory`|Atributo opcional.<br /><br /> Especifica a classe no assembly que é responsável por gerar instâncias de especificado `Task` nome.  O usuário também pode especificar um `TaskBody` como um elemento filho que a fábrica de tarefa recebe e usa para gerar a tarefa.  O conteúdo a `TaskBody` são específicos para a fábrica da tarefa.|  
|`TaskName`|Atributo obrigatório.<br /><br /> O nome da tarefa de referência de um assembly.  Se forem possíveis usar ambiguidades, esse atributo sempre deve especificar namespaces completo.  Se houver ambiguidades, o MSBuild escolhe uma correspondência arbitrária, que pode produzir resultados inesperados.|  
|`Condition`|Atributo opcional.<br /><br /> A condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### Elementos filho  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|O conjunto de parâmetros que aparecem na tarefa que é gerada pelo `TaskFactory`.|  
|[Tarefa](../msbuild/task-element-msbuild.md)|Os dados são passados para o `TaskFactory` para gerar uma instância da tarefa.|  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Projeto](../msbuild/project-element-msbuild.md)|Elemento raiz necessária de um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo de projeto.|  
  
## Comentários  
 Variáveis de ambiente, propriedades de linha de comando e propriedades de nível de projeto podem ser referenciadas em algum lugar do `UsingTask` elemento se ele aparece no arquivo de projeto explicitamente ou por meio de um arquivo de projeto importado.  Para obter mais informações, consulte [ \(tarefas\)](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
>  Propriedades de nível de projeto não têm significado se o `UsingTask` elemento é proveniente de um dos arquivos .tasks globalmente registrados com o mecanismo do MSBuild.  Propriedades de nível de projeto não são globais para MSBuild.  
  
 No MSBuild 4.0, usando as tarefas pode ser carregado de .overridetask arquivos.  
  
## Exemplo  
 O exemplo a seguir mostra como usar o `UsingTask` elemento com um `AssemblyName` atributo.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Exemplo  
 O exemplo a seguir mostra como usar o `UsingTask` elemento com um `AssemblyFile` atributo.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)