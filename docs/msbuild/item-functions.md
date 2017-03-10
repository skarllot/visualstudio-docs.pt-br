---
title: "Fun&#231;&#245;es de itens | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, funções de item"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
caps.handback.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Fun&#231;&#245;es de itens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Iniciando com o MSBuild 4,0, o código nas tarefas e destinos podem chamar funções de item para obter informações sobre os itens no projeto.  Essas funções simplificam obter itens de Distinct\(\) e são mais rápidas do que em loop através dos itens.  
  
## Funções de item de cadeia de caracteres  
 Você pode usar métodos e propriedades de cadeia de caracteres no .NET Framework para operar em qualquer valor do item.  Para métodos de <xref:System.String> , especifique o nome do método.  Para propriedades de <xref:System.String> , especifique o nome da propriedade após o “get\_”.  
  
 Para itens que têm várias cadeias de caracteres, o método da cadeia de caracteres ou blocos de propriedade em cada cadeia de caracteres.  
  
 O exemplo a seguir mostra como usar essas funções de item de cadeia de caracteres.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## Funções intrínsecas de item  
 A tabela a seguir lista as funções intrínsecas disponíveis para itens.  
  
|Função|Exemplo|Descrição|  
|------------|-------------|---------------|  
|`Count`|`@(MyItem->Count())`|Retorna o número de itens.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|retorna o equivalente de `Path.DirectoryName` para cada item.|  
|`Distinct`|`@(MyItem->Distinct())`|Retorna os itens que têm valores diferentes de `Include` .  os metadados são ignorados.  A comparação não difere maiúsculas de minúsculas.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Retorna os itens que têm valores diferentes de `itemspec` .  os metadados são ignorados.  A comparação diferencia maiúsculas de minúsculas.|  
|`Reverse`|`@(MyItem->Reverse())`|Retorna os itens na ordem inversa.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Retorna `boolean` para indicar se qualquer item possui os metadados dados nome e valor.  A comparação não difere maiúsculas de minúsculas.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Retorna itens com seus metadados apagados.  Somente `itemspec` é mantido.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Retorna os itens que têm o nome fornecido de metadados.  A comparação não difere maiúsculas de minúsculas.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Retorna os valores de metadados que têm o nome de metadados.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Retorna os itens que têm metadados dados nome e valor.  A comparação não difere maiúsculas de minúsculas.|  
  
 O exemplo a seguir mostra como usar funções intrínsecas de item.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## Consulte também  
 [Itens](../msbuild/msbuild-items.md)