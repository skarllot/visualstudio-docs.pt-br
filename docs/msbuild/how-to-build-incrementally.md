---
title: Como compilar incrementalmente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
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
ms.openlocfilehash: db5ed1a51108ed5809eb16466e5a782d01c0cef2
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-build-incrementally"></a>Como compilar incrementalmente
Quando você cria um projeto grande, é importante que já tenha criado componentes que ainda estejam atualizados e não sejam recriados. Se todos os destinos forem criados todas as vezes, cada build levará muito tempo para ser concluída. Para habilitar as builds incrementais (builds nos quais somente os destinos que não foram criados antes ou destinos que estão desatualizados são recriadas), o [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) pode comparar os carimbos de data/hora dos arquivos de entrada com carimbos de data/hora dos arquivos de saída e determinar se ignora, compila ou recompila parcialmente um destino. No entanto, deve haver um mapeamento de um para um entre entradas e saídas. Você pode usar transformações para permitir que os destinos identifiquem esse mapeamento direto. Para obter mais informações sobre transformações, consulte [Transformações](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Especificando entradas e saídas  
 Um destino pode ser criado incrementalmente se as entradas e saídas forem especificadas no arquivo de projeto.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Para especificar as entradas e saídas para um destino  
  
-   Use os atributos `Inputs` e `Outputs` do elemento `Target`. Por exemplo:  
  
    ```xml  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 O [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode comparar os carimbos de data/hora dos arquivos de entrada com carimbos de data/hora dos arquivos de saída e determinar se ignora, compila ou recompila parcialmente um destino. No exemplo a seguir, se qualquer arquivo na lista de itens de `@(CSFile)` for mais recente que o arquivo hello.exe, o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] executará o destino; caso contrário, ele será ignorado:  
  
```xml  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Quando entradas e saídas são especificadas em um destino, cada saída pode mapear para apenas uma entrada ou não pode haver nenhum mapeamento direto entre as saídas e entradas. Na [Tarefa Csc](../msbuild/csc-task.md) anterior, por exemplo, a saída, hello.exe, não pode ser mapeada para uma única entrada, ela depende de todas as entradas.  
  
> [!NOTE]
>  Um destino no qual não há nenhum mapeamento direto entre as entradas e saídas sempre será compilado com mais frequência do que um destino no qual cada saída possa mapear para apenas uma entrada porque o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] não pode determinar quais saídas precisam ser recriadas se algumas das entradas tiverem sido alteradas.  
  
 Tarefas nas quais você pode identificar um mapeamento direto entre as saídas e entradas, como a [Tarefa LC](../msbuild/lc-task.md), são mais adequadas para builds incrementais, ao contrário de tarefas como `Csc` e [Vbc](../msbuild/vbc-task.md), que produzem um assembly de saída de diversas entradas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um projeto que cria arquivos de ajuda para um sistema de ajuda hipotético. O projeto funciona convertendo arquivos de origem .txt em arquivos .content intermediários, que são então combinados com os arquivos de metadados XML para produzir o arquivo final .help usado pelo sistema de Ajuda. O projeto usa as seguintes tarefas hipotéticas:  
  
-   `GenerateContentFiles`: converte arquivos .txt em arquivos .content.  
  
-   `BuildHelp`: combina arquivos .content e arquivos de metadados XML para criar o arquivo .help final.  
  
 O projeto usa transformações para criar um mapeamento de um para um entre entradas e saídas na tarefa `GenerateContentFiles`. Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md). Além disso, o elemento `Output` é configurado para usar automaticamente as saídas da tarefa `GenerateContentFiles` como entradas para a tarefa `BuildHelp`.  
  
 Este arquivo de projeto contém os destinos `Convert` e `Build`. As tarefas `GenerateContentFiles` e `BuildHelp` são colocadas nos destinos `Convert` e `Build`, respectivamente, para que cada destino possa ser compilado de forma incremental. Ao usar o elemento `Output`, as saídas da tarefa `GenerateContentFiles` são colocadas na lista de itens de `ContentFile`, na qual elas podem ser usadas como entradas para a tarefa `BuildHelp`. Usar o elemento `Output` dessa maneira fornece automaticamente as saídas de uma tarefa como entradas para outra tarefa para que você não precise listar os itens individuais ou listas de itens manualmente em cada tarefa.  
  
> [!NOTE]
>  Embora o destino `GenerateContentFiles` possa ser compilado incrementalmente, todas as saídas desse destino sempre serão necessárias como entradas para o destino `BuildHelp`. O [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece automaticamente todas as saídas de um destino como entradas para outro destino quando você usa o elemento `Output`.  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Transformações](../msbuild/msbuild-transforms.md)   
 [Tarefa Csc](../msbuild/csc-task.md)   
 [Tarefa Vbc](../msbuild/vbc-task.md)
