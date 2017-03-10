---
title: "Elemento ImportGroup (MSBuild) | Microsoft Docs"
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
  - "Elemento <ImportGroup> [MSBuild]"
  - "Elemento ImportGroup [MSBuild]"
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento ImportGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contém uma coleção de `Import` elementos que estão agrupados sob uma condição opcional.  Para obter mais informações, consulte [Elemento Import \(MSBuild\)](../msbuild/import-element-msbuild.md).  
  
## Sintaxe  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Condition`|Atributo opcional.<br /><br /> A condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### Elementos filho  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Importar](../msbuild/import-element-msbuild.md)|Importa o conteúdo de um arquivo de projeto para outro arquivo de projeto.|  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Project](../msbuild/project-element-msbuild.md)|Elemento raiz necessários de um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo de projeto.|  
  
## Comentários  
  
## Exemplo  
 O seguinte código exemplo mostra a `ImportGroup` elemento.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Itens](../msbuild/msbuild-items.md)