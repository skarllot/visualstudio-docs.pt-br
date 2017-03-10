---
title: "Metadados de itens na separa&#231;&#227;o de destinos em lotes | Microsoft Docs"
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
  - "MSBuild, lote de destino"
  - "lote de destino [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Metadados de itens na separa&#231;&#227;o de destinos em lotes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tem a capacidade de executar análises de dependência sobre as entradas e saídas de um destino de compilação.  Se for determinado que as entradas ou saídas do destino estejam atualizadas, o destino será ignorado e a compilação irá prosseguir.  `Target`elementos de usar o `Inputs` e `Outputs` atributos para especificar os itens para inspecionar durante a análise de dependência.  
  
 Se um destino contém uma tarefa que usa em lote de itens como entradas ou saídas, o `Target` o elemento de destino deve usar o processamento em lotes no seu `Inputs` ou `Outputs` atributos para habilitar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para ignorar os lotes de itens que já estão atualizados.  
  
## Destinos de processamento em lotes  
 O exemplo a seguir contém uma lista de itens chamada `Res` que é dividido em dois lotes com base na `Culture` metadados do item.  Cada um desses lotes é passada para o `AL` tarefa, que cria um assembly de saída para cada lote.  Usando o processamento em lotes na `Outputs` atributo da `Target` elemento, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode determinar se cada um dos lotes individuais é atualizada antes de executar o destino.  Sem o processamento em lotes de destino, ambos os lotes de itens seriam executados pela tarefa sempre que o destino foi executado.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [Como compilar incrementalmente](../msbuild/how-to-build-incrementally.md)   
 [Separação em lotes](../msbuild/msbuild-batching.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Metadados de itens na separação de tarefas em lotes](../msbuild/item-metadata-in-task-batching.md)