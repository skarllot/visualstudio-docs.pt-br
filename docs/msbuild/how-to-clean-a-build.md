---
title: Como limpar um build | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
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
ms.openlocfilehash: f0deda8dae333bcb778085456c49cfd53f067254
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-clean-a-build"></a>Como limpar um build
Quando você limpa um build, todos os arquivos de saída e intermediários são excluídos, deixando apenas os arquivos de projeto e componente. Nos arquivos de projeto e de componente, novas instâncias dos arquivos de saída e intermediários podem ser criadas. A biblioteca de tarefas comuns fornecida com o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclui uma tarefa [Exec](../msbuild/exec-task.md) que você pode usar para executar comandos do sistema. Para obter mais informações sobre a biblioteca de tarefas, consulte [Referência de Tarefa](../msbuild/msbuild-task-reference.md).  
  
## <a name="creating-a-directory-for-output-items"></a>Criando um diretório para itens de saída  
 Por padrão, o arquivo .exe que é criado quando você compila um projeto é colocado no mesmo diretório dos arquivos de projeto e código-fonte. No entanto, normalmente, itens de saída são criados em um diretório separado.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Para criar um diretório para itens de saída  
  
1.  Use o elemento `Property` para definir o local e o nome do diretório. Por exemplo, crie um diretório chamado `BuiltApp` no diretório que contém os arquivos de projeto e código-fonte:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Use a tarefa [MakeDir](../msbuild/makedir-task.md) para criar o diretório se o diretório não existir. Por exemplo:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## <a name="removing-the-output-items"></a>Removendo os itens de saída  
 Antes de criar novas instâncias dos arquivos de saída e intermediários, é possível limpar todas as instâncias anteriores dos arquivos de saída e intermediários. Use a tarefa [RemoveDir](../msbuild/removedir-task.md) para excluir um diretório e todos os arquivos e diretórios que ele contém de um disco.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Para remover um diretório e todos os arquivos contidos no diretório  
  
-   Use a tarefa `RemoveDir` para remover o diretório. Por exemplo:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de projeto de código contém um novo destino, `Clean`, que usa a tarefa `RemoveDir` para excluir um diretório e todos os arquivos e diretórios que ele contém. Também no exemplo, o destino `Compile` cria um diretório separado para os itens de saída que são excluídos quando o build for removida.  
  
 `Compile` é definido como o destino padrão e, portanto, é usado automaticamente a menos que você especifique um ou mais destinos diferentes. Use a opção de linha de comando **/target** para especificar um destino diferente. Por exemplo:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 A opção **/target** pode ser abreviada como **/t** e pode especificar mais de um destino. Por exemplo, para usar o destino `Clean` e, em seguida, o destino `Compile`, digite:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Tarefa Exec](../msbuild/exec-task.md)   
 [Tarefa MakeDir](../msbuild/makedir-task.md)   
 [Tarefa RemoveDir](../msbuild/removedir-task.md)   
 [Tarefa Csc](../msbuild/csc-task.md)   
 [Destinos](../msbuild/msbuild-targets.md)
