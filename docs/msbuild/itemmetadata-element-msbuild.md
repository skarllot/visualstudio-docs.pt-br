---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 817b86aa6bc653305e3eeba9b3e0cf8ec5ed7c93
ms.lasthandoff: 02/22/2017

---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)
Contém uma chave de metadados de item definida pelo usuário, que contém o valor de metadados do item. Um item pode ter qualquer número de pares de chave-valor de metadados.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Sintaxe  

```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos filho  
 nenhuma.  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Um elemento definido pelo usuário que define as entradas para o processo de build.|  

## <a name="text-value"></a>Valor de texto  
 Um valor de texto é opcional.  

 Esse texto Especifica o valor de metadados do item, que pode ser texto ou XML.  

## <a name="remarks"></a>Comentários  

## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar metadados de `Culture` com o valor `fr` ao item `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Itens](../msbuild/msbuild-items.md)

