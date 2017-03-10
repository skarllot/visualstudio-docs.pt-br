---
title: "Elemento ItemMetadata (MSBuild) | Microsoft Docs"
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
  - "Elemento <ItemMetadata> [MSBuild]"
  - "Elemento ItemMetadata [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento ItemMetadata (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contém uma chave de metadados do item definido pelo usuário, que contém o valor de metadados de item.  Um item pode ter qualquer número de pares chave\-valor de metadados.  
  
## Sintaxe  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho, e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada.  Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### Elementos filho  
 Nenhum.  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Item](../msbuild/item-element-msbuild.md)|Um elemento definido pelo usuário que define as entradas para o processo de compilação.|  
  
## Valor de texto  
 Um valor de texto é opcional.  
  
 Esse texto Especifica o valor de metadados de item, que pode ser um texto ou XML.  
  
## Comentários  
  
## Exemplo  
 O exemplo de código a seguir mostra como adicionar `Culture` metadados com o valor `fr` para o item `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Itens](../msbuild/msbuild-items.md)