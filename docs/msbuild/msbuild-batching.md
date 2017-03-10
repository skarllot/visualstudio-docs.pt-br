---
title: "Separa&#231;&#227;o em lotes no MSBuild | Microsoft Docs"
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
  - "lote [MSBuild]"
  - "MSBuild, lote"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Separa&#231;&#227;o em lotes no MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tem a capacidade de dividir as listas de itens em categorias diferentes, ou de lotes, com base nos metadados de item e executar uma tarefa ou destino uma vez com cada lote.  
  
## Tarefa em lotes  
 Tarefas em lote permite que você simplifique seus arquivos de projeto, fornecendo uma maneira de dividir as listas de itens em lotes diferentes e passar cada um desses lotes em uma tarefa separadamente.  Isso significa que um arquivo de projeto só precisa ter a tarefa e seus atributos declarados uma vez, embora ele possa ser executado várias vezes.  
  
 Especificar que você deseja [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para executar o processamento em lotes com uma tarefa usando o %\(*ItemMetaDataName*\) a notação em um dos atributos de tarefa.  O exemplo seguinte divide a `Example` lista de itens em lotes com base na `Color` valor de metadados de item e passa os lotes para o `MyTask` tarefas separadamente.  
  
> [!NOTE]
>  Se você fizer referência a lista de itens em qualquer lugar nos atributos de tarefa ou o nome de metadados pode ser ambíguo, você pode usar o %\(*ItemCollection.ItemMetaDataName*\) notação para qualificar totalmente o valor de metadados do item para processamento em lotes.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Para exemplos de lotes mais específicos, consulte [Metadados de itens na separação de tarefas em lotes](../msbuild/item-metadata-in-task-batching.md).  
  
## Lotes de destino  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]verifica se as entradas e saídas de um destino estão atualizadas antes de executar o destino.  Se as entradas e saídas estão atualizadas, o destino será ignorado.  Se uma tarefa dentro de um destino usa o processamento em lotes, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] precisa determinar se as entradas e saídas para cada lote de itens é atualizada.  Caso contrário, o destino é executado sempre que é atingido.  
  
 A exemplo a seguir mostra um `Target` elemento que contém um `Outputs` de atributo com o %\(*ItemMetaDataName*\) notação.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]divide o `Example` lista de itens em lotes com base na `Color` os metadados do item e analisar os carimbos de hora dos arquivos de saída para cada lote.  Se as saídas de um lote não estão atualizadas, o destino é executado.  Caso contrário, o destino é ignorado.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Outro exemplo de destino em lote, consulte [Metadados de itens na separação de destinos em lotes](../msbuild/item-metadata-in-target-batching.md).  
  
## Funções de propriedade usando metadados  
 Processamento em lotes pode ser controlado por funções de propriedade incluem metadados.  Por exemplo,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 usa <xref:System.IO.Path.Combine%2A> para combinar um caminho de pasta raiz com um caminho de compilação de item.  
  
 Funções de propriedade não podem aparecer dentro de valores de metadados.  Por exemplo,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 não é permitido.  
  
 Para obter mais informações sobre funções de propriedade, consulte [Funções de propriedades](../msbuild/property-functions.md).  
  
## Consulte também  
 [Elemento ItemMetadata \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)