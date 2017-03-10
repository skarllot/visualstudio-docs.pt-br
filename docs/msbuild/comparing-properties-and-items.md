---
title: "Comparando propriedades e itens | Microsoft Docs"
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
  - "MSBuild, propriedades do msbuild"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comparando propriedades e itens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Itens e propriedades de MSBuild são usados para passar informações para tarefas, avaliar condições e armazenar os valores que podem ser referenciadas em todo o arquivo de projeto.  
  
-   Propriedades são pares nome-valor. Para obter mais informações, consulte [Propriedades MSBuild](../msbuild/msbuild-properties.md).  
  
-   Os itens são objetos que representam os arquivos normalmente. Objetos de item podem ter associados a coleções de metadados. Metadados são pares nome-valor. Para obter mais informações, consulte [itens](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Escalares e vetores  
 Como propriedades do MSBuild são pares de nome-valor que têm apenas um valor de cadeia de caracteres, eles geralmente são descritos como *escalares*. Como tipos de item do MSBuild são listas de itens, eles geralmente são descritos como *vetor*. No entanto, na prática, propriedades podem representar vários valores e tipos de item podem ter zero ou itens.  
  
### <a name="target-dependency-injection"></a>Injeção de dependência de destino  
 Para ver como propriedades podem representar vários valores, considere um padrão de uso comum para adicionar um destino para uma lista de destinos a serem compilados. Normalmente, essa lista é representada por um valor de propriedade, com os nomes de destino, separados por ponto e vírgula.  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 O `BuildDependsOn` propriedade normalmente é usada como o argumento de um destino `DependsOnTargets` atributo, efetivamente convertê-la em uma lista de itens. Essa propriedade pode ser substituída para adicionar um destino ou para alterar a ordem de execução de destino. Por exemplo,  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Adiciona o destino CustomBuild à lista de destinos, dando `BuildDependsOn` o valor `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 Começando com o MSBuild 4.0, injeção de dependência de destino foi preterida. Use o `AfterTargets` e `BeforeTargets` atributos em vez disso. Para obter mais informações, consulte [ordem de compilação de destino](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Conversões entre cadeias de caracteres e listas de itens  
 MSBuild executa conversões entre tipos de itens e valores de cadeia de caracteres conforme necessário. Para ver como uma lista de itens pode se tornar um valor de cadeia de caracteres, considere o que acontece quando um tipo de item é usado como o valor de uma propriedade de MSBuild:  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 O tipo de item OutputDir tem um `Include` atributo com o valor "arquivos-chave\\; Certificados\\". MSBuild analisa essa cadeia de caracteres em dois itens: certificados e KeyFiles\\\. Quando o tipo de item OutputDir é usado como o valor da propriedade OutputDirList, MSBuild converte ou o tipo de item para a cadeia de caracteres separados por ponto e vírgula "nivela" "arquivos-chave\\; Certificados\\".  
  
## <a name="properties-and-items-in-tasks"></a>Propriedades e itens de tarefas  
 Itens e as propriedades são usadas como entradas e saídas de tarefas do MSBuild. Para obter mais informações, consulte [tarefas](../msbuild/msbuild-tasks.md).  
  
 Propriedades são passadas para tarefas como atributos. Dentro da tarefa, uma propriedade de MSBuild é representada por um tipo de propriedade cujo valor pode ser convertido em uma cadeia de caracteres. Os tipos de propriedade com suporte incluem `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, e qualquer tipo que <xref:System.Convert.ChangeType%2A> pode manipular.  
  
 Itens são passados para tarefas como <xref:Microsoft.Build.Framework.ITaskItem> objetos. Dentro da tarefa, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> representa o valor do item e <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> recupera seus metadados.  
  
 A lista de itens de um tipo de item pode ser passada como uma matriz de `ITaskItem` objetos. Começando com o .NET Framework 3.5, itens podem ser removidos de uma lista de itens em um destino usando o `Remove` atributo. Como itens podem ser removidos de uma lista de itens, é possível para um tipo de item com zero itens. Se uma lista de itens é passada para uma tarefa, o código da tarefa deve verificar essa possibilidade.  
  
## <a name="property-and-item-evaluation-order"></a>Propriedade e ordem de classificação do Item  
 Durante a fase de avaliação de uma compilação, os arquivos importados são incorporados a compilação na ordem em que aparecem. Itens e as propriedades são definidas em três passos na seguinte ordem:  
  
-   Propriedades são definidas e modificadas na ordem em que aparecem.  
  
-   Definições de item são definidas e modificadas na ordem em que aparecem.  
  
-   Itens são definidos e modificados na ordem em que aparecem.  
  
 Durante a fase de execução de uma compilação, os itens que são definidos em destinos e as propriedades são avaliados juntos em uma única fase na ordem em que aparecem.  
  
 No entanto, isso não é a história completa. Quando uma propriedade, a definição do item ou o item é definido, seu valor é avaliado. O avaliador de expressão expande a cadeia de caracteres que especifica o valor. A expansão de cadeia de caracteres depende da fase de criação. Aqui está uma ordem de avaliação de propriedade e o item mais detalhada:  
  
-   Durante a fase de avaliação de uma compilação:  
  
    -   Propriedades são definidas e modificadas na ordem em que aparecem. Funções de propriedade são executadas. Valores de propriedade em $(PropertyName) o formulário são expandidas dentro de expressões. O valor da propriedade é definido como a expressão expandida.  
  
    -   Definições de item são definidas e modificadas na ordem em que aparecem. Funções de propriedade já foram expandidas dentro de expressões. Valores de metadados são definidos para as expressões expandidas.  
  
    -   Tipos de item são definidos e modificados na ordem em que aparecem. Valores no formulário de item @(ItemType) são expandidos. Transformações de item também são expandidas. Valores e funções de propriedade já foi expandidos em expressões. Os valores de lista e os metadados de item são definidos para as expressões expandidas.  
  
-   Durante a fase de execução de uma compilação:  
  
    -   Itens que são definidos em destinos e as propriedades são avaliados juntos na ordem em que aparecem. Funções de propriedade são executadas e valores de propriedade são expandidos dentro de expressões. Valores de item e transformações de item também são expandidas. Os valores de propriedade, os valores de tipo de item e valores de metadados são definidos para as expressões expandidas.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Efeitos sutis da ordem de avaliação  
 Na fase de avaliação de uma compilação, a avaliação da propriedade precede avaliação do item. No entanto, propriedades podem ter valores que aparecem depende de valores de item. Considere o seguinte script.  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Executando a tarefa de mensagem exibe esta mensagem:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Isso ocorre porque o valor de `KeyFileVersion` é, na verdade, a cadeia de caracteres "@(KeyFile->'%(Version)')". Item e transformações de item não foram expandidas quando a propriedade foi definida pela primeira vez, para que o `KeyFileVersion` propriedade foi atribuída o valor da cadeia de caracteres não expandida.  
  
 Durante a fase de execução da compilação, ao processar a tarefa de mensagem, o MSBuild expande a cadeia de caracteres "@(KeyFile->'%(Version)')" para produzir "1.0.0.3".  
  
 Observe que a mesma mensagem seria exibido mesmo se os grupos de propriedade e item foram revertidos na ordem.  
  
 Como um segundo exemplo, considere o que pode acontecer quando grupos de propriedade e item estão localizados em destinos:  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 A tarefa de mensagem exibe esta mensagem:  
  
```  
KeyFileVersion:   
```  
  
 Isso ocorre porque durante a fase de execução da compilação, são avaliados propriedade e item grupos definidos em destinos de cima para baixo ao mesmo tempo. Quando `KeyFileVersion` estiver definido, `KeyFile` é desconhecido. Portanto, a transformação de item se expande para uma cadeia de caracteres vazia.  
  
 Nesse caso, invertendo a ordem dos grupos de propriedade e item restaura a mensagem original:  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 O valor de `KeyFileVersion` é definido como "1.0.0.3" e não ao "@(KeyFile->'%(Version)')". tarefa a mensagem exibe esta mensagem:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)