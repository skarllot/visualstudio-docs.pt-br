---
title: "Constructos condicionais do MSBuild | Microsoft Docs"
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
  - "Elemento <Choose> [MSBuild]"
  - "Elemento <Otherwise> [MSBuild]"
  - "Elemento <When> [MSBuild]"
  - "Elemento Choose [MSBuild]"
  - "construtores condicionais [MSBuild]"
  - "MSBuild, construtores condicionais"
  - "Elemento Otherwise [MSBuild]"
  - "Elemento When [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Constructos condicionais do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]Fornece um mecanismo para um \/ ou processamento com o  [Escolha](../msbuild/choose-element-msbuild.md),  [quando](../msbuild/when-element-msbuild.md), e  [caso contrário](../msbuild/otherwise-element-msbuild.md) elementos.  
  
## Usando o elemento de escolha  
 O `Choose` elemento contém uma série de `When` elementos com `Condition` atributos que são testados em ordem de cima para baixo até ser avaliada como um `true`.  Se mais de um `When` elemento é avaliada como `true`, apenas a primeira é usada.  Um `Otherwise` elemento, se presente, será avaliado se nenhuma condição em uma `When` elemento é avaliada como `true`.  
  
 `Choose`elementos podem ser usados como elementos filhos do `Project`, `When` e `Otherwise` elementos.  `When`e `Otherwise` elementos podem ter `ItemGroup`, `PropertyGroup`, ou `Choose` elementos filho.  
  
## Exemplo  
 O exemplo a seguir usa a `Choose` e `When` elementos para um \/ ou processamento.  As propriedades e os itens do projeto são definidas, dependendo do valor da `Configuration` propriedade.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
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
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## Consulte também  
 [Elemento Choose \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [Elemento When \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Elemento Otherwise \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)