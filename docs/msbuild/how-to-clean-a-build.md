---
title: "Como limpar uma compila&#231;&#227;o | Microsoft Docs"
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
  - "diretórios [.NET Framework], para itens de saída"
  - "tarefa Exec [MSBuild]"
  - "MSBuild, limpando uma compilação"
  - "saída, removendo itens"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como limpar uma compila&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao limpar uma compilação, todos os arquivos de saída e intermediários são excluídos, deixando somente os arquivos de projeto e o componente.  Dos arquivos de projeto e de componente, arquivos de saída e de novas instâncias de intermediários podem então ser criados.  A biblioteca de tarefas comuns que é fornecido com o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclui um  [Exec](../msbuild/exec-task.md) tarefa que você pode usar para executar comandos do sistema.  Para obter mais informações sobre a biblioteca de tarefas, consulte [Referência de tarefas](../msbuild/msbuild-task-reference.md).  
  
## A criação de um diretório para itens de saída  
 Por padrão, o arquivo. exe que é criado quando você compila um projeto é colocado no mesmo diretório dos arquivos de origem e projeto.  No entanto, normalmente, itens de saída são criados em um diretório separado.  
  
#### Para criar um diretório para itens de saída  
  
1.  Use o `Property` elemento para definir o local e o nome do diretório.  Por exemplo, crie um diretório chamado `BuiltApp` no diretório que contém os arquivos de origem e de projeto:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Use o  [MakeDir](../msbuild/makedir-task.md) tarefas para criar o diretório se o diretório não existir.  Por exemplo:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## Remover os itens de saída  
 Para criar novas instâncias de arquivos de saída e intermediários, você talvez queira limpar anteriores de todas as instâncias de arquivos de saída e intermediários.  Use o  [RemoveDir](../msbuild/removedir-task.md) tarefa para excluir um diretório e todos os arquivos e diretórios que ele contém a partir de um disco.  
  
#### Para remover um diretório e todos os arquivos contidos no diretório  
  
-   Use o `RemoveDir` tarefa para remover o diretório.  Por exemplo:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## Exemplo  
 O seguinte código exemplo de projeto contém um novo destino, `Clean`, que usa a `RemoveDir` tarefa para excluir um diretório e todos os arquivos e diretórios que ele contém.  Também neste exemplo, o `Compile` destino cria um diretório separado para os itens de saída que são excluídos quando a compilação estiver limpo.  
  
 `Compile`é definido como o destino padrão e, portanto, é usado automaticamente a menos que você especifique um destino diferente ou destinos.  Usar a opção de linha de comando **\/target** para especificar um destino diferente.  Por exemplo:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 O **\/target** switch pode ser reduzido a **\/t** e pode especificar mais de um destino.  Por exemplo, para usar o destino `Clean` , em seguida, o destino `Compile`, tipo:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Tarefa Exec](../msbuild/exec-task.md)   
 [Tarefa MakeDir](../msbuild/makedir-task.md)   
 [Tarefa RemoveDir](../msbuild/removedir-task.md)   
 [Tarefa Csc](../msbuild/csc-task.md)   
 [Destinos](../msbuild/msbuild-targets.md)