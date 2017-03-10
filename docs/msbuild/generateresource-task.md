---
title: "Tarefa GenerateResource | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa GenerateResource [MSBuild]"
  - "MSBuild, Tarefa GenerateResource"
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GenerateResource
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Converte entre. txt e arquivos. resx \(formato de recurso baseado em XML\) e arquivos. Resources binário comuns de runtime de linguagem que podem ser incorporados em um executável binário de tempo de execução ou compilados em assemblies satélites.  Esta tarefa é normalmente usada para converter arquivos. txt ou. resx. Resource arquivos.  O `GenerateResource` tarefa é funcionalmente semelhante a  [Resgen. exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `GenerateResource` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AdditionalInputs`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Contém entradas adicionais para verificação de dependência feito por esta tarefa.  Por exemplo, os arquivos de projeto e destinos normalmente devem ser entradas, para que se elas forem atualizadas, todos os recursos são geradas novamente.|  
|`EnvironmentVariables`|Opcional `String[]` parâmetro.<br /><br /> Especifica uma matriz de pares nome\-valor de variáveis que devem ser passadas para o Resgen. exe gerado, além dos ambiente \(ou substituindo seletivamente\) o bloco de ambiente regular.|  
|`ExcludedInputPaths`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica uma matriz dos itens que especificam os caminhos do qual as entradas controladas serão ignoradas durante a verificação atualizado.|  
|`ExecuteAsTool`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, executa Tlbimp. exe e aximp. exe a partir do destino apropriado framework fora do processo para gerar os assemblies de invólucro necessários.  Esse parâmetro permite multi\-direcionamento de `ResolveComReferences`.|  
|`FilesWritten`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém os nomes de todos os arquivos gravados em disco.  Isso inclui o arquivo de cache, se houver.  Este parâmetro é útil para implementações de limpar.|  
|`MinimalRebuildFromTracking`|Opcional `Boolean` parâmetro.<br /><br /> Obtém ou define uma opção que especifica se controladas compilação incremental será usada.  Se `true`, compilação incremental é ativada; Caso contrário, será forçada uma recompilação.|  
|`NeverLockTypeAssemblies`|Opcional `Boolean` parâmetro.<br /><br /> Especifica o nome dos arquivos gerados, como arquivos. Resources.  Se você não especificar um nome, o nome do arquivo de entrada correspondente é usado e o arquivo. resources criado é colocado no diretório que contém o arquivo de entrada.|  
|`OutputResources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Especifica o nome dos arquivos gerados, como arquivos. Resources.  Se você não especificar um nome, o nome do arquivo de entrada correspondente é usado e o arquivo. resources criado é colocado no diretório que contém o arquivo de entrada.|  
|`PublicClass`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, cria uma classe strongly typed como uma classe pública.|  
|`References`|Opcional `String[]` parâmetro.<br /><br /> Referências ao carregar tipos de arquivos. resx do.  Elementos de dados de arquivo resx podem ter um.NET associado.  Quando o arquivo. resx é lido, isso deve ser resolvido.  Normalmente, ele é resolvido com êxito usando o tipo padrão de carregamento de regras.  Se você fornecer os assemblies no `References`, elas terão prioridade.<br /><br /> Este parâmetro não é necessário para recursos fortemente tipados.|  
|`SdkToolsPath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho para as ferramentas do SDK, como, por exemplo, Resgen. exe.|  
|`Sources`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os itens para converter.  Os itens passados para este parâmetro devem ter uma das seguintes extensões de arquivo:<br /><br /> -   `.txt`: Especifica a extensão de um arquivo de texto converter.  Arquivos de texto só podem conter recursos de seqüência de caracteres.<br />-   `.resx`: Especifica a extensão de um arquivo de recurso baseado em XML converter.<br />-   `.restext`: Especifica o mesmo formato como. txt.  Essa extensão diferente é útil se você desejar distinguir claramente os arquivos de origem que contêm recursos de outros arquivos de origem no seu processo de compilação.<br />-   `.resources`: Especifica a extensão de um arquivo de recurso converter.|  
|`StateFile`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o caminho para um arquivo de cache opcional que é usado para acelerar a verificação de links em arquivos de entrada. resx de dependência.|  
|`StronglyTypedClassName`|Opcional `String` parâmetro.<br /><br /> Especifica o nome da classe para a classe de recurso fortemente tipado.  Se este parâmetro não for especificado, o nome de base do arquivo de recurso é usado.|  
|`StronglyTypedFilename`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o nome do arquivo de origem.  Se este parâmetro não for especificado, o nome da classe é usado como o nome do arquivo base, com a extensão dependente de idioma.  Por exemplo: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Opcional `String` parâmetro.<br /><br /> Especifica o idioma a ser usado ao gerar a fonte de classe strongly typed Resources.  Este parâmetro deve corresponder ao exatamente um dos idiomas usados pela CodeDomProvider.  For example: `VB` or `C#`.<br /><br /> Passando um valor para esse parâmetro, você pode instruir a tarefa para gerar recursos fortemente tipados.|  
|`StronglyTypedManifestPrefix`|Opcional `String` parâmetro.<br /><br /> Especifica o prefixo de namespace ou o manifesto de recurso a ser usado na fonte de classe gerada para o recurso com rigidez de tipos.|  
|`StronglyTypedNamespace`|Opcional `String` parâmetro.<br /><br /> Especifica o namespace a ser usado para a fonte da classe gerada para o recurso com rigidez de tipos.  Se este parâmetro não for especificado, todos os recursos com rigidez de tipos estão no namespace global.|  
|`TLogReadFiles`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro somente leitura.<br /><br /> Obtém uma matriz de itens que representam a leitura dos logs de controle.|  
|`TLogWriteFiles`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro somente leitura.<br /><br /> Obtém uma matriz de itens que representam a gravação dos logs de controle.|  
|`ToolArchitecture`|Opcional [String](assetId:///String?qualifyHint=False&autoUpgrade=True) parâmetro.<br /><br /> Usado para determinar se precisa ou não Tracker.exe a ser usado para gerar Resgen. exe.<br /><br /> Deve ser analisável um membro da <xref:Microsoft.Build.Utilities.ExecutableType> enumeração.  Se `String.Empty`, usa uma heurística para determinar uma arquitetura de padrão.  Deve ser analisável a um membro da enumeração Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Opcional assetId:///String?qualifyHint=False&autoUpgrade=True parâmetro.<br /><br /> Especifica o caminho para o apropriado.Local do NET Framework que contém FileTracker.dll.<br /><br /> Se o conjunto, o usuário assume a responsabilidade por certificando\-se de que o número de bits do FileTracker.dll que eles passam coincide com o número de bits do Resgen. exe que pretendem usar.  Se não for definido, a tarefa decide o local apropriado com base na atual.NET Framework versão.|  
|`TrackerLogDirectory`|Opcional assetId:///String?qualifyHint=False&autoUpgrade=True parâmetro.<br /><br /> Especifica o diretório intermediário no qual os logs de rastreamento de executar esta tarefa serão colocados.|  
|`TrackerSdkPath`|Opcional assetId:///String?qualifyHint=False&autoUpgrade=True parâmetro.<br /><br /> Especifica o caminho para o local apropriado do SDK do Windows que contém Tracker.exe.<br /><br /> Se o conjunto, o usuário assume a responsabilidade por certificando\-se de que o número de bits do Tracker.exe que eles passam coincide com o número de bits do Resgen. exe que pretendem usar.  Se não for definido, a tarefa decide o local apropriado com base no SDK do Windows atual.|  
|`TrackFileAccess`|Opcional [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) parâmetro.<br /><br /> Se verdadeiro, o diretório do arquivo de entrada é usado para resolver os caminhos de arquivo relativos.|  
|`UseSourcePath`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, especifica que o diretório do arquivo de entrada deverá ser usado para resolver os caminhos de arquivo relativos.|  
  
## Comentários  
 Porque os arquivos. resx podem conter links para outros arquivos de recurso, não é suficiente simplesmente comparar carimbos de arquivo. resx e. Resource para ver se as saídas estão atualizadas.  Em vez disso, o `GenerateResource` tarefa segue os links nos arquivos. resx e verifica os carimbos de hora dos arquivos vinculados.  Isso significa que você não deve geralmente usar `Inputs` e `Outputs` atributos no destino que contém o `GenerateResource` de tarefas, como isso pode fazer com que ela seja ignorada quando, na verdade, ele deve ser executado.  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
 Ao usar o MSBuild 4.0 para o destino.NET 3.5 projetos, a compilação pode falhar em x86 recursos.  Para contornar esse problema, você pode construir o destino como assembly Qualquer\_cpu.  
  
## Exemplo  
 O exemplo a seguir usa a `GenerateResource` para gerar os arquivos. Resources dos arquivos especificados pelo `Resx` item da coleção.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 O `GenerateResource` tarefa utiliza \<LogicalName\> metadados de \<EmbeddedResource\> item para nomear o recurso que está incorporado em um assembly.  
  
 Supondo que o assembly chamado myAssembly, o código a seguir gera um recurso incorporado chamado someQualifier.someResource.resources:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Sem \<LogicalName\> metadados, o recurso seria nomeado myAssembly.myResource.resources.  Este exemplo aplica\-se somente para o processo de compilação de Visual Basic e C\# Visual.  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)