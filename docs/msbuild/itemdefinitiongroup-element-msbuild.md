---
title: "Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Elemento <ItemDefinitionGroup> [MSBuild]"
  - "Elemento ItemDefinitionGroup [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento ItemDefinitionGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `ItemDefinitionGroup` elemento permite que você defina um conjunto de definições de Item, que são valores de metadados que são aplicados a todos os itens no projeto, por padrão.  ItemDefinitionGroup substitui a necessidade de usar o [Tarefa CreateItem](../msbuild/createitem-task.md) e o [Tarefa CreateProperty](../msbuild/createproperty-task.md).  Para obter mais informações, consulte [Definições de itens](../msbuild/item-definitions.md).  
  
## Sintaxe  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Condition`|Atributo opcional.  Condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### Elementos filho  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Item](../msbuild/item-element-msbuild.md)|Define as entradas para o processo de compilação.  Pode haver zero ou mais `Item` elementos em um `ItemDefinitionGroup`.|  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Project](../msbuild/project-element-msbuild.md)|Elemento raiz necessários de um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo de projeto.|  
  
## Exemplo  
 O exemplo de código a seguir define dois itens de metadados, m e n, em um ItemDefinitionGroup.  Neste exemplo, os metadados padrão "m" é aplicado ao Item "i" como "m" de metadados não é definido explicitamente pelo Item "i".  No entanto, metadados padrão "n" não é aplicado ao Item "i", porque os metadados "n" já está definido pelo Item "i".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Itens](../msbuild/msbuild-items.md)