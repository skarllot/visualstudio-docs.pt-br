---
title: "Como selecionar os arquivos a serem compilados | Microsoft Docs"
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
  - "atributo Include [MSBuild]"
  - "MSBuild, incluindo arquivos"
  - "MSBuild, curingas"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como selecionar os arquivos a serem compilados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você compilação um projeto que contém vários arquivos, você pode listar cada arquivo separadamente no arquivo de projeto , ou você pode usar caracteres curinga para incluir todos os arquivos em um diretório ou um conjunto aninhado de diretórios.  
  
## Especificando entradas  
 Itens representam as entradas para a compilação.  Para obter mais informações sobre itens, consulte [Itens](../msbuild/msbuild-items.md).  
  
 Para incluir os arquivos para a compilação, devem ser incluídos em uma lista de item na [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]arquivo de projeto .   Vários arquivos podem ser adicionados às listas de item , incluindo os arquivos individualmente ou usando caracteres curinga para incluir vários arquivos ao mesmo tempo.  
  
#### Para declarar os itens individualmente  
  
-   Use o `Include` atributos semelhantes ao seguinte:  
  
     `<CSFile Include="form1.cs"/>`  
  
     \- ou \-  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Se os itens de um itemdecoleção não estiverem no mesmo diretório do arquivo de projeto , você deve especificar completa ou caminho relativo do item.   Por exemplo: `Include="..\..\form2.cs"`.  
  
#### Para declarar vários itens  
  
-   Use o `Include` atributos semelhantes ao seguinte:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     \- ou \-  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## Especificando entradas com caracteres curinga  
 Você também pode usar caracteres curinga recursivamente incluem todos os arquivos ou apenas a arquivos específicos de subdiretórios como entradas para a compilação.  Para obter mais informações sobre caracteres curinga, consulte[Itens](../msbuild/msbuild-items.md)  
  
 Os exemplos a seguir baseiam\-se em um projeto que contém os arquivos de gráficos nos seguintes diretórios e subdiretórios, com o arquivo de projeto localizado no diretório do projeto:  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### Para incluir todos os arquivos. jpg no diretório Images e subdiretórios  
  
-   Use o seguinte `Include` atributo:  
  
     `Include="Images\**\*.jpg"`  
  
#### Para incluir todos os arquivos. jpg, começando com "img"  
  
-   Use o seguinte `Include` atributo:  
  
     `Include="Images\**\img*.jpg"`  
  
#### Para incluir todos os arquivos em diretórios com nomes que terminam em "jpgs"  
  
-   Use um dos seguintes `Include` atributos:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     \- ou \-  
  
     `Include="Images\**\*jpgs\*"`  
  
## Itens de passagem para uma tarefa  
 Em um arquivo de projeto , você pode usar o @ notação \(\) em tarefas para especificar uma lista de todo o item como a entrada para a compilação.  Se você lista todos os arquivos separadamente ou utilize caracteres curinga, você pode usar essa notação.  
  
#### Para usar todos os arquivos do Visual C\# ou Visual Basic como entradas  
  
-   Use o `Include` atributos semelhantes à seguinte:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     \- ou \-  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Você deve usar caracteres curinga com itens para especificar as entradas para a compilação; não é possível especificar as entradas usando o `Sources` atributo na [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de tarefas, como  [Csc](../msbuild/csc-task.md) ou  [arquivo Vbc](../msbuild/vbc-task.md).   O exemplo a seguir não é válido em um arquivo de projeto :  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## Exemplo  
 O exemplo de código a seguir mostra um projeto que inclui todos os arquivos de entrada separadamente.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Exemplo  
 O exemplo de código a seguir usa um caractere curinga para incluir todos os arquivos. cs.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Como excluir arquivos da compilação](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Itens](../msbuild/msbuild-items.md)