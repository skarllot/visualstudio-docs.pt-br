---
title: "Itens do MSBuild | Microsoft Docs"
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
  - "MSBuild, itens"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Itens do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Itens do MSBuild são entradas no sistema de compilação, e eles normalmente representam arquivos. Itens são agrupados em tipos de item com base em seus nomes de elemento. Tipos de item são denominados listas de itens que podem ser usados como parâmetros para tarefas. As tarefas usam os valores do item para executar as etapas do processo de compilação.  
  
 Porque os itens são nomeados pelo tipo de item ao qual eles pertencem, os termos "item" e "valor do item" podem ser usados alternadamente.  
  
 **Neste tópico**  
  
-   [Criar itens em um arquivo de projeto](#BKMK_Creating1)  
  
-   [Criando itens durante a execução](#BKMK_Creating2)  
  
-   [Referenciando itens em um arquivo de projeto](#BKMK_ReferencingItems)  
  
-   [Usando caracteres curinga para especificar itens](#BKMK_Wildcards)  
  
-   [Usando o atributo de exclusão](#BKMK_ExcludeAttribute)  
  
-   [Metadados de item](#BKMK_ItemMetadata)  
  
    -   [Metadados de Item de referência em um arquivo de projeto](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadados de itens conhecidos](#BKMK_WellKnownItemMetadata)  
  
    -   [Transformando os tipos de Item por meio de metadados](#BKMK_Transforming)  
  
-   [Definições de item](#BKMK_ItemDefinitions)  
  
-   [Atributos de itens em um ItemGroup de um destino](#BKMK_AttributesWithinTargets)  
  
    -   [Remova o atributo](#BKMK_RemoveAttribute)  
  
    -   [Atributo KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Atributo RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Atributo KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Criar itens em um arquivo de projeto  
 Declarar itens no arquivo de projeto como filho elementos de um [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elemento. O nome do elemento filho é o tipo do item. O `Include` atributo do elemento Especifica os itens (arquivos) para ser incluído com esse tipo de item. Por exemplo, o XML a seguir cria um tipo de item chamado `Compile`, que inclui dois arquivos.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 O item "file2.cs" não substituir o item "file1.cs"; em vez disso, o nome do arquivo é acrescentado à lista de valores para o `Compile` tipo de item. Você não pode remover um item de um tipo de item durante a fase de avaliação de uma compilação.  
  
 O XML a seguir cria o mesmo tipo de item, declarando os dois arquivos em um `Include` atributo. Observe que os nomes de arquivo são separados por ponto e vírgula.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Criando itens durante a execução  
 Itens que estão fora [destino](../msbuild/target-element-msbuild.md) elementos são atribuídos valores durante a fase de avaliação de uma compilação. Durante a fase de execução subsequentes, os itens podem ser criados ou modificados das seguintes maneiras:  
  
-   Qualquer tarefa pode emitir um item. A emissão de um item, o [tarefa](../msbuild/task-element-msbuild.md) elemento deve ter um filho [saída](../msbuild/output-element-msbuild.md) elemento que possui um `ItemName` atributo.  
  
-   O [CreateItem](../msbuild/createitem-task.md) tarefa pode emitir um item. Esse uso é preterido.  
  
-   A partir do .NET Framework 3.5, `Target` elementos podem conter [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementos que podem conter elementos de item.  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Referenciando itens em um arquivo de projeto  
 Para referenciar tipos de item em todo o arquivo de projeto, use a sintaxe @(`ItemType`). Por exemplo, você faria referência no exemplo anterior, o tipo de item usando `@(Compile)`. Usando esta sintaxe, você pode passar itens para tarefas, especificando o tipo de item como um parâmetro dessa tarefa. Para obter mais informações, consulte [como: selecione os arquivos de compilação](../msbuild/how-to-select-the-files-to-build.md).  
  
 Por padrão, os itens de um tipo de item são separados por ponto e vírgula (;) quando ele é expandido. Você pode usar a sintaxe @(*ItemType*, '*separador*') para especificar um separador diferente do padrão. Para obter mais informações, consulte [como: exibir um Item de lista separada por vírgulas](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Usando caracteres curinga para especificar itens  
 Você pode usar o * *, \*, e? caracteres curinga para especificar um grupo de arquivos como entradas para uma compilação em vez de listar cada arquivo separadamente.  
  
-   O? caractere curinga corresponde a um único caractere.  
  
-   O * corresponde a zero ou mais caracteres de caractere curinga.  
  
-   O * corresponde a sequência de caracteres curinga um caminho parcial.  
  
 Por exemplo, você pode especificar todos os arquivos. cs na pasta que contém o arquivo de projeto usando o seguinte elemento no arquivo de projeto.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 O elemento a seguir seleciona todos os arquivos. vb na unidade d::  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Para obter mais informações sobre caracteres curinga, consulte [como: selecione os arquivos de compilação](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Usando o atributo de exclusão  
 Elementos de item podem conter o `Exclude` atributo, que exclui itens específicos (arquivos) do tipo de item. O `Exclude` atributo normalmente é usado junto com caracteres curinga. Por exemplo, o XML a seguir adiciona cada arquivo. cs no diretório para o tipo de item de CSFile, exceto o `DoNotBuild.cs` arquivo.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 O `Exclude` atributo afeta somente os itens que são adicionados a `Include` atributo no elemento do item que contém os dois. O exemplo a seguir não excluir o arquivo Form1. cs, que foi adicionado no elemento do item anterior.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Para obter mais informações, consulte [como: excluir arquivos da compilação](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> Metadados de item  
 Itens que podem conter metadados além das informações de `Include` e `Exclude` atributos. Esses metadados podem ser usados por tarefas que requerem mais informações sobre os itens ou destinos e tarefas em lotes. Para obter mais informações, consulte [lotes](../msbuild/msbuild-batching.md).  
  
 Metadados são uma coleção de pares chave-valor que são declarados no arquivo de projeto como elementos filhos de um elemento do item. O nome do elemento filho é o nome dos metadados, e o valor do elemento filho é o valor dos metadados.  
  
 Os metadados são associados ao elemento do item que o contém. Por exemplo, o XML a seguir adiciona `Culture` metadados que tem o valor `Fr` "one.cs" e "two.cs" itens do CSFile o tipo de item.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Um item pode ter zero ou mais valores de metadados. Você pode alterar os valores de metadados a qualquer momento. Se você definir metadados para um valor vazio, você efetivamente removê-lo da compilação.  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Metadados de Item de referência em um arquivo de projeto  
 Você pode fazer referência a metadados em todo o arquivo de projeto usando a sintaxe %(`ItemMetadataName`). Se existir a ambiguidade, você pode qualificar uma referência usando o nome do tipo de item. Por exemplo, você pode especificar %(*ItemType.ItemMetaDataName*). O exemplo a seguir usa os metadados de exibição para a tarefa de mensagens de lote. Para obter mais informações sobre como usar os metadados do item para envio em lote, consulte [metadados de Item no lote de tarefas](../msbuild/item-metadata-in-task-batching.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Metadados de itens conhecidos  
 Quando um item é adicionado a um tipo de item, esse item é atribuído alguns metadados bem conhecidos. Por exemplo, todos os itens que os metadados sejam conhecidos `%(Filename)`, cujo valor é o nome do item. Para obter mais informações, consulte [Well-Known metadados de Item](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Transformando os tipos de Item por meio de metadados  
 Você pode transformar listas de itens em listas de item novo usando metadados. Por exemplo, você pode transformar um tipo de item `CppFiles` que tem itens que representam arquivos. cpp em uma lista de arquivos. obj correspondente usando a expressão `@(CppFiles -> '%(Filename).obj')`.  
  
 O código a seguir cria um `CultureResource` que contém cópias de todos os tipo de item `EmbeddedResource` itens com `Culture` metadados. O `Culture` metadados valor se torna o valor dos metadados do novo `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Para obter mais informações, consulte [transforma](../msbuild/msbuild-transforms.md).  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Definições de item  
 A partir do .NET Framework 3.5, você pode adicionar metadados padrão para qualquer tipo de item usando o [elemento ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Como metadados conhecidos, os metadados padrão estão associado a todos os itens do tipo de item que você especificar. Você pode substituir explicitamente metadados padrão em uma definição de item. Por exemplo, o XML a seguir fornece o `Compile` "one.cs" e "three.cs" os metadados de itens `BuildDay` com o valor "Segunda-feira". O código fornece o item "two.cs" os metadados `BuildDay` com o valor "Terça-feira".  
  
```  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Para obter mais informações, consulte [definições de Item](../msbuild/item-definitions.md).  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Atributos de itens em um ItemGroup de um destino  
 A partir do .NET Framework 3.5, `Target` elementos podem conter [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementos que podem conter elementos de item. Os atributos nesta seção são válidos quando elas são especificadas de um item em uma `ItemGroup` em um `Target`.  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Remova o atributo  
 Itens em uma `ItemGroup` de um destino pode conter o `Remove` atributo, que remove itens específicos (arquivos) do tipo de item. Esse atributo foi introduzido no .NET Framework 3.5.  
  
 O exemplo a seguir remove todos os arquivos. config do tipo de item de compilação.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Atributo KeepMetadata  
 Se um item for gerado em um destino, o elemento de item pode conter o `KeepMetadata` atributo. Se esse atributo for especificado, apenas os metadados que é especificado na lista de nomes separados por ponto-e-vírgula serão transferidos para o item de destino do item de origem. Um valor vazio para esse atributo equivale a não especificá-lo. O `KeepMetadata` atributo foi introduzido no .NET Framework 4.5.  
  
 O exemplo a seguir ilustra como usar o `KeepMetadata` atributo.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Atributo RemoveMetadata  
 Se um item for gerado em um destino, o elemento de item pode conter o `RemoveMetadata` atributo. Se esse atributo for especificado, as todos os metadados são transferidos do item de origem para o item de destino, exceto metadados cujos nomes estão contidos na lista de nomes separados por ponto-e-vírgula. Um valor vazio para esse atributo equivale a não especificá-lo. O `RemoveMetadata` atributo foi introduzido no .NET Framework 4.5.  
  
 O exemplo a seguir ilustra como usar o `RemoveMetadata` atributo.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Atributo KeepDuplicates  
 Se um item for gerado em um destino, o elemento de item pode conter o `KeepDuplicates` atributo. `KeepDuplicates` é um `Boolean` atributo que especifica se um item deve ser adicionado ao grupo de destino se o item for uma duplicata exata de um item existente.  
  
 Se o item de origem e destino tiverem o mesmo valor de inclusão mas metadados diferentes, o item será adicionado mesmo se `KeepDuplicates` for definido como `false`. Um valor vazio para esse atributo equivale a não especificá-lo. O `KeepDuplicates` atributo foi introduzido no .NET Framework 4.5.  
  
 O exemplo a seguir ilustra como usar o `KeepDuplicates` atributo.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)   
 [Como: selecione os arquivos de compilação](../msbuild/how-to-select-the-files-to-build.md)   
 [Como: excluir arquivos da compilação](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Como: exibir uma lista de itens separada por vírgulas](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definições de item](../msbuild/item-definitions.md)   
 [Envio em lote](../msbuild/msbuild-batching.md)   
 [Elemento item (MSBuild)](../msbuild/item-element-msbuild.md)