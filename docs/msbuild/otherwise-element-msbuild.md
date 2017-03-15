---
title: Elemento Otherwise (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 9
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
ms.openlocfilehash: ce7adee8cd2c64fb9bca5df27dc436a22452f60c
ms.lasthandoff: 02/22/2017

---
# <a name="otherwise-element-msbuild"></a>Elemento Otherwise (MSBuild)
Especifica o bloco de código a executar se e somente se as condições de todos os elementos `When` forem avaliadas como `false`.  

 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>Sintaxe  

```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  
 nenhuma.  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento opcional.<br /><br /> Avalia elementos filhos para selecionar uma seção do código para executar. Pode ser que não haja nenhum ou mais de um elemento `Choose` em um elemento `Otherwise`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contém um conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos pelo usuário. Pode ser que não haja nenhum ou mais de um elemento `ItemGroup` em um elemento `Otherwise`.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contém um conjunto de definidos elementos [Property](../msbuild/property-element-msbuild.md) definidos pelo usuário. Pode ser que não haja nenhum ou mais de um elemento `PropertyGroup` em um elemento `Otherwise`.|  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Avalia elementos filhos para selecionar uma seção do código para executar.|  

## <a name="remarks"></a>Comentários  
 Pode haver apenas um elemento `Otherwise` em um elemento `Choose` e ele deve ser o último elemento.  

 Os elementos `Choose`, `When` e `Otherwise` são usados juntos para fornecer uma maneira de selecionar uma seção de código para executar entre diversas possíveis alternativas. Para obter mais informações, consulte [Constructos condicionais](../msbuild/msbuild-conditional-constructs.md).  

## <a name="example"></a>Exemplo  
 O projeto a seguir usa o elemento `Choose` para selecionar qual conjunto de valores de propriedade nos elementos `When` definir. Se os atributos `Condition` de ambos elementos `When` forem avaliadas como `false`, os valores de propriedade no elemento `Otherwise` serão definidos.  

```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
        </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  

## <a name="see-also"></a>Consulte também  
 [Constructos condicionais](../msbuild/msbuild-conditional-constructs.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)

