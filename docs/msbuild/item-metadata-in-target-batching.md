---
title: "Metadados de itens na separação de destinos em lotes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
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
ms.openlocfilehash: 5b8bc0b724adfd5d012aef0c527a494adddb902b
ms.lasthandoff: 02/22/2017

---
# <a name="item-metadata-in-target-batching"></a>Metadados de itens na separação de destinos em lotes
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tem a capacidade de executar a análise de dependência em entradas e saídas de um destino de build. Se for determinado que as entradas ou saídas do destino estão atualizadas, o destino será ignorado e o build continuará. Elementos `Target` usam os atributos `Inputs` e `Outputs` para especificar os itens a fim de inspecionar durante a análise de dependência.  
  
 Se um destino contiver uma tarefa que usa itens em lotes como entradas ou saídas, o elemento `Target` do destino deve usar o envio em lote nos aributos `Inputs` ou `Outputs` para habilitar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a ignorar lotes de itens que já estão atualizados.  
  
## <a name="batching-targets"></a>Envio em lote de destinos  
 O exemplo a seguir contém uma lista de item nomeada `Res` que é dividida em dois lotes baseados nos metadados de item `Culture`. Cada um desses lotes é passada para a tarefa `AL`, que cria um assembly de saída para cada lote. Ao usar o envio em lote no atributo `Outputs` do elemento `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode determinar se cada um dos lotes individuais está atualizado antes de executar o destino. Sem o uso do envio em lote de destino, ambos os lotes de itens seriam executados pela tarefa toda vez que o destino fosse executado.  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Como compilar incrementalmente](../msbuild/how-to-build-incrementally.md)   
 [Envio em lote](../msbuild/msbuild-batching.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadados de itens na separação de tarefas em lotes](../msbuild/item-metadata-in-task-batching.md)
