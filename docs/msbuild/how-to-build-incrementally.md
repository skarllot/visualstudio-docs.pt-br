---
title: "Como compilar incrementalmente | Microsoft Docs"
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
  - "compilações incrementais"
  - "MSBuild, compilando incrementalmente"
  - "MSBuild, compilações incrementais"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como compilar incrementalmente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você cria um grande projeto, é importante que componentes criados anteriormente que ainda são atualizados não são recriados.  Se todos os destinos são compilados todas as vezes, cada compilação terá um longo tempo para concluir.  para ativar as compilações incrementais \(compilações em que somente os destinos que não sejam compilados antes ou destinos que são expirado, são reconstruídas\), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \(\)[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]pode comparar os carimbos de data\/hora dos arquivos de entrada com os carimbos de data\/hora dos arquivos de saída e determinar se ignorar, compilar, ou recrie parcialmente um destino.  Em o entanto, deve haver um mapeamento um\-para\-um entre a entrada e saída.  Você pode usar transformações para ativar destinos para identificar esse mapeamento direto.  Para obter mais informações sobre transformações, consulte [Transformações](../msbuild/msbuild-transforms.md).  
  
## Especificando entrada e saída  
 Um destino pode ser compilado incremental se entradas e saída são especificadas no arquivo de projeto.  
  
#### Para especificar entrada e saída para um destino  
  
-   Use os atributos de `Inputs` e de `Outputs` do elemento de `Target` .  Por exemplo:  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode comparar os carimbos de data\/hora dos arquivos de entrada com os carimbos de data\/hora dos arquivos de saída e determinar se ignorar, compilar, ou recrie parcialmente um destino.  Em o exemplo, se qualquer arquivo na lista de itens de `@(CSFile)` é mais recente que o arquivo hello.exe, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] executará o destino; : se não será tiver ignorado  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Quando as entradas e saída são especificadas em um destino, ou cada saída pode mapear a apenas uma entrada ou não pode haver nenhum mapeamento entre direto a saída e as entradas.  Em [Tarefa Csc](../msbuild/csc-task.md)anterior, por exemplo, a saída, hello.exe, não pode ser mapeado para uma única entrada – depende dos.  
  
> [!NOTE]
>  Um destino que não há nenhum mapeamento direto entre as entradas e saída compilarão sempre mais freqüência do que um destino que cada saída pode mapear a apenas uma entrada como [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] não pode determinar qual saídas precisam ser reconstruídas se quaisquer das entradas foram alterados.  
  
 As tarefas na qual você pode identificar um mapeamento entre direto a saída e entradas, como [Tarefa LC](../msbuild/lc-task.md), são mais adequadas para compilações incrementais, ao contrário das tarefas como `Csc` e [Vbc](../msbuild/vbc-task.md), que geram um conjunto de saída de um número de entradas.  
  
## Exemplo  
 O seguinte exemplo usa um projeto que ajudam as compilações arquivos para um sistema de ajuda hipotético.  Convertendo o projeto trabalha a fonte arquivo .txt nos arquivos intermediários de .content, que são combinados em com os arquivos de metadados XML para gerar o arquivo final de .help usado pelo sistema de ajuda.  O projeto usa as seguintes tarefas: hipotéticas  
  
-   `GenerateContentFiles`: Converte arquivos .txt em arquivos de .content.  
  
-   `BuildHelp`: Arquivos das combina .content e de metadados de arquivos XML para criar o arquivo final de .help.  
  
 O projeto tornam\-se para criar um mapeamento um\-para\-um entre a entrada e saída na tarefa de `GenerateContentFiles` .  Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md).  Além de isso, o elemento de `Output` é configurado para usar automaticamente a tarefa de `GenerateContentFiles` como as entradas para a tarefa de `BuildHelp` .  
  
 Esse arquivo de projeto contém os destinos de `Convert` e de `Build` .  As tarefas de `GenerateContentFiles` e de `BuildHelp` são colocadas nos destinos de `Convert` e de `Build` respectivamente de modo que cada destino pode ser compilado incremental.  Usando o elemento de `Output` , a tarefa de `GenerateContentFiles` são colocadas na lista de itens de `ContentFile` , onde eles podem ser usadas como entrada para a tarefa de `BuildHelp` .  Usar o elemento de `Output` de essa maneira fornece automaticamente a saída de uma tarefa como as entradas para outra tarefa que você não tenha que listar itens individuais ou liste o item manualmente em cada tarefa.  
  
> [!NOTE]
>  Embora o destino de `GenerateContentFiles` pode criar incremental, todas as saídas do destino sempre são necessárias como entradas para o destino de `BuildHelp` .  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece automaticamente todas as saídas de um destino como entradas para outro destino quando você usa o elemento de `Output` .  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Transformações](../msbuild/msbuild-transforms.md)   
 [Tarefa Csc](../msbuild/csc-task.md)   
 [Tarefa Vbc](../msbuild/vbc-task.md)