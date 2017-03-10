---
title: "Como estender o processo de compila&#231;&#227;o do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, Propriedades DependsOn"
  - "MSBuild, estendendo compilações do Visual Studio"
  - "MSBuild, substituindo propriedades DependsOn"
  - "MSBuild, substituindo destinos predefinidos"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como estender o processo de compila&#231;&#227;o do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] processo de compilação é definido por uma série de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivos. targets importados para seu arquivo de projeto.  Um desses arquivos importados, Microsoft.Common.targets, pode ser estendido para permitir a execução de tarefas personalizadas em vários pontos no processo de compilação.  Este tópico explica dois métodos que você pode usar para estender o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] processo de compilação:  
  
-   Substituindo destinos predefinidos específicos definidos no Microsoft.Common.targets.  
  
-   Substituindo as propriedades de "DependsOn" definidas na Microsoft.Common.targets.  
  
## Substituindo destinos predefinidos  
 O arquivo Microsoft.Common.targets contém um conjunto de destinos vazios predefinidos que são chamadas antes e depois de alguns dos principais alvos no processo de compilação.  Por exemplo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] chamadas de `BeforeBuild` destino principal antes de `CoreBuild` destino e o `AfterBuild` de destino após a `CoreBuild` destino.  Por padrão, os destinos vazios Microsoft.Common.targets não fazem nada, mas pode substituir o comportamento padrão definindo os destinos que você deseja em um arquivo de projeto importa Microsoft.Common.targets.  Fazendo isso, você pode usar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarefas para dar mais controle sobre o processo de compilação.  
  
#### Para substituir um destino predefinido  
  
1.  Identifica um destino predefinido no Microsoft.Common.targets que você deseja substituir.  Consulte a tabela abaixo lista completa de destinos que você pode ignorar com segurança.  
  
2.  Definir o destino ou destinos no final do seu arquivo de projeto, imediatamente antes do `</Project>` marca.  Por exemplo:  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  Crie o arquivo de projeto.  
  
 A tabela a seguir mostra todos os destinos no Microsoft.Common.targets você pode ignorar com segurança.  
  
|Nome de destino|Descrição|  
|---------------------|---------------|  
|`BeforeCompile`, `AfterCompile`|Tarefas inseridas em um desses destinos executadas antes ou após a compilação principal.  A maioria das personalizações são feitas em um desses dois destinos.|  
|`BeforeBuild`, `AfterBuild`|Tarefas inseridas em um desses destinos serão executado antes ou depois de tudo na compilação. **Note:**  O `BeforeBuild` e `AfterBuild` destinos já estão definidos em comentários no final da maioria dos arquivos de projeto.  Isso permite que você facilmente adicionar eventos de pré e pós\-compilação para seu arquivo de projeto.|  
|`BeforeRebuild`, `AfterRebuild`|Tarefas inserido em um desses destinos executados antes ou depois que o núcleo recompilar funcionalidade é chamado.  É a ordem de execução de destino em Microsoft.Common.targets: `BeforeRebuild`, `Clean`, `Build`e `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Tarefas inseridas em um desses destinos executados antes ou após o núcleo funcionalidade limpa é invocada.|  
|`BeforePublish`, `AfterPublish`|Tarefas inserido em um desses destinos executados antes ou depois que o núcleo publicar funcionalidade é chamado.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Tarefas inseridas em um desses destinos executadas antes ou depois de referências de assembly são resolvidas.|  
|`BeforeResGen`, `AfterResGen`|Tarefas inseridas em um desses destinos executadas antes ou depois de recursos são gerados.|  
  
## Substituindo "DependsOn" propriedades  
 Substituir destinos predefinidos é uma maneira fácil para estender o processo de compilação, mas porque [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] avalia a definição de alvos seqüencialmente, não há nenhuma maneira de impedir que outro projeto que importa seu projeto substituam os destinos já substituída.  Isso, por exemplo, o último `AfterBuild` destino definido no arquivo de projeto, depois de todos os outros projetos foram importados, será aquele que é usado durante a compilação.  
  
 Contra substituições indesejadas de destinos, substituindo as propriedades de "DependsOn" são usadas em `DependsOnTargets` atributos em todo o arquivo Microsoft.Common.targets.  Por exemplo, o `Build` destino contém um `DependsOnTargets` valor do atributo `"$(BuildDependsOn)"`.  Considere:  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Esta parte do XML indica que antes de `Build` pode executar o destino, todos os destinos especificados na `BuildDependsOn` propriedade deve ser executado primeira.  O `BuildDependsOn` propriedade é definida como:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Você pode substituir esse valor de propriedade, declarando outra propriedade chamada `BuildDependsOn` no final do seu arquivo de projeto.  Incluindo anterior `BuildDependsOn` propriedade na nova propriedade, você pode adicionar novos destinos para o início e fim da lista de destino.  Por exemplo:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 Projetos que importar seus arquivos de projeto podem substituir essas propriedades sem substituir as personalizações que você fez.  
  
#### Substituir uma propriedade "DependsOn"  
  
1.  Identifica uma propriedade "DependsOn" predefinida na Microsoft.Common.targets que você deseja substituir.  Consulte a tabela abaixo para obter uma lista das propriedades comumente substituído "DependsOn".  
  
2.  Defina outra instância da propriedade ou propriedades no final do seu arquivo de projeto.  Incluir a propriedade original, por exemplo `$(BuildDependsOn)`, na nova propriedade.  
  
3.  Defina seus destinos personalizados antes ou após a definição da propriedade.  
  
4.  Crie o arquivo de projeto.  
  
### Propriedades de "DependsOn" normalmente substituídas  
  
|Nome da propriedade|Descrição|  
|-------------------------|---------------|  
|`BuildDependsOn`|A propriedade para substituir se quiser inserir destinos personalizados antes ou após o processo de compilação inteira.|  
|`CleanDependsOn`|A propriedade para substituir se quiser limpar saída de personalizar seu processo de compilação.|  
|`CompileDependsOn`|A propriedade para substituir se quiser inserir processos personalizados antes ou após a etapa de compilação.|  
  
## Consulte também  
 [Integração com o Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Arquivos .Targets](../msbuild/msbuild-dot-targets-files.md)