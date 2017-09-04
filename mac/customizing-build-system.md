---
title: Personalizando o Sistema de Build
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: c261dbc285da6f488e6a328c997e2a9563c1c73a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="customizing-the-build-system"></a>Personalizando o sistema de build

O MSbuild é um mecanismo de build desenvolvido pela Microsoft que permite compilar aplicativos primariamente .NET. A estrutura Mono também tem sua própria implementação do Build Engine da Microsoft, chamado **xbuild**. No entanto, o xbuild foi desativado para dar lugar ao uso do MSBuild em todos os sistemas operacionais.

O **MSbuild** é usado principalmente como sistema de build para projetos no Visual Studio para Mac. 

O MSBuild funciona obtendo um conjunto de entradas, como arquivos de origem, e transformando-os em saídas, como arquivos executáveis, e gera essa saída invocando ferramentas como o compilador. 


## <a name="msbuild-file"></a>Arquivo do MSBuild

O MSBuild usa um arquivo XML, chamado de arquivo de projeto, que define os *Itens* que fazem parte do seu projeto (como recursos de imagem) e as *Propriedades* necessárias para compilar o projeto. Este arquivo de projeto sempre terá uma extensão de arquivo terminando em `proj`, como `.csproj` para projetos C#. 

### <a name="viewing-the-msbuild-file"></a>Exibindo o arquivo do MSBuild
Você pode localizar esse arquivo clicando com o botão direito do mouse no nome do projeto e selecionando **Revelar no localizador**. Isso exibirá todos os arquivos e pastas relacionadas ao seu projeto, incluindo o arquivo `.csproj`, conforme ilustrado abaixo:

![](media/customizing-build-system-image1.png)

Você também pode exibir o `.csproj` em uma nova guia no Visual Studio para Mac clicando com o botão direito do mouse no nome do projeto e navegando até **Ferramentas > Editar arquivo**:

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Composição do arquivo do MSBuild

Todos os arquivos do MSBuild contêm um elemento de raiz obrigatório `Project`, conforme mostrado abaixo:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Normalmente, o projeto também importará um arquivo `.targets`, que contém muitas das regras que descrevem como processar e compilar os diversos arquivos. Isso geralmente aparece na parte inferior do seu arquivo `proj` e, para projetos C#, será semelhante ao seguinte:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

O arquivo de destino é outro arquivo MSBuild. Este arquivo contém o código MSBuild reutilizável por vários projetos. Por exemplo, o arquivo `Microsoft.CSharp.targets`, que se encontra em um diretório representado pela propriedade `MSBuildBinPath` (ou variável), contém a lógica para compilar assemblies C# com base nos arquivos de origem.

### <a name="items-and-properties"></a>Itens e propriedades

Há dois tipos de dados fundamentais no MSBuild: *itens* e *propriedades*, que são explicados em mais detalhes abaixo.

#### <a name="properties"></a>Propriedades

As propriedades são pares chave/valor, que são usados para armazenar configurações que afetam a compilação, como opções do compilador.

Elas são definidas usando um PropertyGroup e podem conter qualquer número de PropertiesGroups, que pode conter qualquer número de propriedades. 

Por exemplo, o PropertyGroup para um aplicativo de console simples pode ser semelhante ao seguinte:

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

Propriedades podem ser referidas de expressões que usam a sintaxe `$()`. Por exemplo, `$(Foo)` será avaliado como o valor da propriedade `Foo`. Se a propriedade não foi definida, ela será avaliada como uma cadeia de caracteres vazia, sem erros.

#### <a name="items"></a>Itens

Os itens fornecem uma maneira de lidar com entradas para o sistema de build, como listas ou conjuntos e geralmente representam arquivos. Cada item tem um *tipo* e uma *especificação* de item, bem como *metadados* arbitrários opcionais. Observe que o MSBuild não funciona em itens individuais, ele obtém todos os itens de um determinado tipo, chamado *conjunto* de itens

Os itens são criados declarando um `ItemGroup`. Pode haver qualquer quantidade de ItemGroups, que podem conter qualquer quantidade de itens. 

Por exemplo, o trecho de código a seguir cria telas de inicialização do iOS. Elas são do tipo `BundleResource`, com a especificação como o caminho para a imagem:

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 Os conjuntos de itens podem ser referidos de expressões que usam a sintaxe `@()`. Por exemplo, `@(BundleResource)` será avaliado como um conjunto de itens BundleResource, o que inclui todos os itens de BundleResource. Se não houver nenhum item desse tipo, ele ficará vazio e sem erros.

## <a name="resources-for-learning-msbuild"></a>Recursos para conhecer o MSBuild

Os recursos a seguir podem ser usados para conhecer melhor o MSBuild:

* [MSDN – Visão geral](https://msdn.microsoft.com/en-us/library/dd393574.aspx)
* [MSDN – Conceitos](https://msdn.microsoft.com/en-us/library/dd637714.aspx)



