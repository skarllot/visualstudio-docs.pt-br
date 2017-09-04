---
title: Elemento Item (MSBuild) | Microsoft Docs
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
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 31
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 2430531e4ddb3a5ef40cd773327311fa7b85ce48
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---
# <a name="item-element-msbuild"></a>Elemento Item (MSBuild)
Contém um item definido pelo usuário e seus metadados. Cada item usado em um projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve ser especificado como o filho de um elemento `ItemGroup`.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Sintaxe  

```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Especificar metadados como atributos
No MSBuild 15.1 ou posterior, os metadados com um nome que não entra em conflito com a lista atual de atributos podem opcionalmente ser expressos como um atributo.

Por exemplo, para especificar uma lista de pacotes NuGet, você normalmente usará algo parecido com a sintaxe a seguir.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

No entanto, é possível passar os metadados `Version` como um atributo, como na seguinte sintaxe:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`Include`|Atributo obrigatório.<br /><br /> O arquivo ou curinga a ser incluído na lista de itens.|  
|`Exclude`|Atributo opcional.<br /><br /> O arquivo ou curinga a ser excluído da lista de itens.|  
|`Condition`|Atributo opcional.<br /><br /> A condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
|`Remove`|Atributo opcional.<br /><br /> O arquivo ou curinga a ser removido da lista de itens.<br /><br />|  
|`KeepDuplicates`|Atributo opcional.<br /><br /> Especifica se um item deverá ser adicionado ao grupo de destino se for uma duplicata exata de um item existente. Se o item de origem e de destino tiverem o mesmo valor `Include`, mas metadados diferentes, o item será adicionado mesmo se `KeepDuplicates` estiver definido como `false`. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).<br /><br /> Esse atributo será válido apenas se for especificado para um item em uma `ItemGroup` que esteja em um `Target`.|  
|`KeepMetadata`|Atributo opcional.<br /><br /> Os metadados dos itens de origem a serem adicionados nos itens de destino. Apenas os metadados cujos nomes são especificados na lista delimitada por ponto e vírgula são transferidos de um item de origem para um item de destino. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).<br /><br /> Esse atributo será válido apenas se for especificado para um item em uma `ItemGroup` que esteja em um `Target`.|  
|`RemoveMetadata`|Atributo opcional.<br /><br /> Os metadados dos itens de origem que não serão transferidos para os itens de destino. Todos os metadados são transferidos de um item de origem para um item de destino, exceto metadados cujos nomes estejam contidos na lista de nomes separados por ponto e vírgula. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).<br /><br /> Esse atributo será válido apenas se for especificado para um item em uma `ItemGroup` que esteja em um `Target`.|  
|`Update`|Atributo opcional. (Disponível somente para projetos do .NET Core no Visual Studio 2017 ou posterior.)<br /><br /> Permite modificar os metadados de um arquivo que foi incluído com o uso de um glob.<br /><br />  Esse atributo será válido apenas se for especificado para um item em um `ItemGroup` que não esteja em um `Target`.|  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Uma chave de metadados de item definido pelo usuário, que contém o valor de metadados do item. Pode ser que não haja nenhum ou mais de um elemento `ItemMetadata` em um item.|  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento grouping para itens.|  

## <a name="remarks"></a>Comentários  
 Os elementos `Item` definem entradas no sistema de compilação e são agrupados em coleções de itens com base em seus nomes de coleção definida pelo usuário. Essas coleções de itens podem ser usadas como parâmetros para [tarefas](../msbuild/msbuild-tasks.md), que usam os itens individuais nas coleções para executar as etapas do processo de build. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).  

 O uso da notação `@(`*myType*`)` permite que uma coleção de itens do tipo *myType* seja expandida em uma lista de cadeias de caracteres delimitada por ponto e vírgula e passada para um parâmetro. Se o parâmetro for do tipo `string`, então o valor do parâmetro será a lista de elementos, separados por ponto e vírgula. Se o parâmetro for uma matriz de cadeias de caracteres (`string[]`), então cada elemento será inserido na matriz com base na localização dos pontos e vírgulas. Se o parâmetro de tarefa for do tipo <xref:Microsoft.Build.Framework.ITaskItem>`[]`, então o valor é o conteúdo da coleção de itens juntamente com quaisquer metadados anexados. Para delimitar cada item usando um caractere que não seja ponto e vírgula, use a sintaxe `@(`*myType*`, '`*separator*`')`.  

 O mecanismo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode avaliar curingas como `*` e `?`, bem como curingas recursivos como `/**/*.cs`. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Exemplos  
 O exemplo de código a seguir mostra como declarar dois itens do tipo `CSFile`. O segundo item declarado contém metadados que possuem `MyMetadata` definidos como `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
O exemplo de código a seguir mostra como usar o atributo `Update` para modificar os metadados em um arquivo chamado somefile.cs que foi incluído por meio de um glob. (Disponível somente para projetos do .NET Core no Visual Studio 2017 ou posterior.)

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Consulte também  
 [Itens](../msbuild/msbuild-items.md)   
 [Propriedades do MSBuild](../msbuild/msbuild-properties.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)

