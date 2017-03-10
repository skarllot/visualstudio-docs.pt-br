---
title: "Elemento OnError (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Elemento <OnError [MSBuild]"
  - "Elemento OnError [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento OnError (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Faz com que um ou vários destinos executar, se o atributo de `ContinueOnError` é `false` para uma tarefa falha.  
  
## Sintaxe  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem elementos filho, atributos, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Condition`|atributo opcional.<br /><br /> Condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atributo necessário.<br /><br /> Destinos para executar uma tarefa se falhar.  Destinos separados de vários com ponto\-e\-vírgula.  Os vários destinos são executados na ordem especificada.|  
  
### Elementos filho  
 Nenhum.  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Destino](../msbuild/target-element-msbuild.md)|Elemento contêiner para tarefas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  
  
## Comentários  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] executa o elemento de `OnError` se uma das tarefas de elemento de `Target` falha com o atributo de `ContinueOnError` definido como `ErrorAndStop` \(ou a `false`\).  Quando a tarefa falhar, destinos especificados no atributo de `ExecuteTargets` são executados.  Se houver mais de um elemento de `OnError` no destino, os elementos de `OnError` são executados seqüencialmente quando a tarefa falhar.  
  
 Para obter informações sobre o atributo de `ContinueOnError` , consulte [Elemento Task \(MSBuild\)](../msbuild/task-element-msbuild.md).  Para obter informações sobre destinos, consulte [Destinos](../msbuild/msbuild-targets.md).  
  
## Exemplo  
 O código a seguir executa as tarefas de `TaskOne` e de `TaskTwo` .  Se `TaskOne` falhar, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avalia o elemento de `OnError` e executa o destino de `OtherTarget` .  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)