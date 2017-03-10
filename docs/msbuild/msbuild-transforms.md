---
title: "Transforma&#231;&#245;es do MSBuild | Microsoft Docs"
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
  - "MSBuild, transformações"
  - "transformações [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Transforma&#231;&#245;es do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Uma transformação é uma conversão individual da lista de um item para outro.  Além de habilitar um projeto converter listas de itens, uma transformação permite um destino identificar um mapeamento direto entre suas entradas e saídas.  Este tópico explica as transformações e como [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa para construir projetos com mais eficiência.  
  
## Transformar modificadores  
 As transformações não são arbitrárias, mas limitadas pela sintaxe especial no qual todos os modificadores de transformação devem ser no formato %\(*ItemMetaDataName*\).  Metadados do item podem ser usado como um modificador de transformação.  Isso inclui os metadados de item conhecido que é atribuído a cada item quando ele é criado.  Para obter uma lista de metadados do item conhecidas, consulte [Metadados de itens conhecidos](../msbuild/msbuild-well-known-item-metadata.md).  
  
 No exemplo a seguir, uma lista de arquivos. resx é transformada em uma lista de arquivos. Resources.  O modificador de transformação %\(filename\) Especifica que cada arquivo. Resources tem o mesmo nome de arquivo do arquivo. resx correspondente.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  Você pode especificar um separador personalizado para uma lista de itens transformados da mesma maneira que você especificar um separador para obter uma lista de item padrão.  Por exemplo, para separar uma lista de itens transformados usando uma vírgula \(,\) em vez de vírgula padrão \(;\), use o seguinte XML.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Por exemplo, se os itens na lista de itens @\(RESXFile\) `Form1.resx`, `Form2.resx`, e `Form3.resx`, as saídas da lista transformado será `Form1.resources`, `Form2.resources`, e `Form3.resources`.  
  
## Usando vários modificadores  
 Uma expressão de transformação pode conter vários modificadores, que podem ser combinados em qualquer ordem e podem ser repetidas.  No exemplo a seguir, o nome do diretório que contém os arquivos é alterado mas os arquivos mantêm a extensão de nome de arquivo e o nome original.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Por exemplo, se os itens que estão contidos na `RESXFile` lista item são `Project1\Form1.resx`, `Project1\Form2.resx`, e `Project1\Form3.text`, saídas na lista transformada será `Toolset\Form1.resx`, `Toolset\Form2.resx`, e `Toolset\Form3.text`.  
  
## Análise de dependência  
 Transformações garantem um mapeamento individual entre a lista de itens transformados e a lista do item original.  Portanto, se um destino cria saídas são transformações das entradas, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode analisar os carimbos de entradas e saídas e decidir se deve ignorar, criar ou reconstruir parcialmente um destino.  
  
 No [Tarefa Copy](../msbuild/copy-task.md) no exemplo a seguir, todos os arquivos do `BuiltAssemblies` lista item mapeia para um arquivo na pasta de destino da tarefa especificada usando uma transformação no `Outputs` atributo.  Se um arquivo a `BuiltAssemblies` item alterações na lista, o `Copy` tarefa será executada apenas para o arquivo alterado e todos os outros arquivos serão ignorados.  Para obter mais informações sobre como usar transformações e análise de dependência, consulte [Como compilar incrementalmente](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## Exemplo  
  
### Descrição  
 A exemplo a seguir mostra um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo de projeto usa transformações.  Este exemplo assume que há apenas um arquivo. xsd no diretório c:\\sub0\\sub1\\sub2\\sub3 e que o diretório de trabalho é c:\\sub0.  
  
### Código  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### Comentários  
 O exemplo produz a seguinte saída.  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Como compilar incrementalmente](../msbuild/how-to-build-incrementally.md)