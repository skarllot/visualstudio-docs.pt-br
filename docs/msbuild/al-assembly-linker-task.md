---
title: "Tarefa AL (Assembly Linker) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AL"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tarefa AL [MSBuild]"
  - "MSBuild, tarefa AL"
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa AL (Assembly Linker)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A tarefa de AL envolve AL.exe, uma ferramenta que é destinado com [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Essa ferramenta do assembly linker é usada para criar um assembly com um manifesto de um ou mais arquivos que são módulos ou arquivos de recurso.  Compiladores e ambientes de desenvolvimento ainda podem fornecer esses recursos, de forma que geralmente não é necessário usar diretamente esta tarefa.  O vinculador assembly é mais útil para os desenvolvedores que precisam criar um único conjunto de módulos \(assembly\) de vários arquivos componentes, como aqueles que podem ser geradas de desenvolvimento de misto linguagem.  Esta tarefa não combina os módulos em um único arquivo do assembly; módulos individuais distribuídos e ainda devem estar disponíveis para o assembly resultante carregue corretamente.  Para obter mais informações sobre AL.exe, consulte [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros de tarefa de `AL` .  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AlgorithmID`|Parâmetro opcional de `String` .<br /><br /> Especifica um algoritmo de hash todos os arquivos em um assembly multi\-arquivos exceto o arquivo que contém o manifesto do assembly.  Para mais informações, consulte a documentação para a opção de `/algid` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`BaseAddress`|Parâmetro opcional de `String` .<br /><br /> Especifica o endereço em uma DLL que será carregado no computador do usuário em tempo de execução.  Os aplicativos usam mais rapidamente se você especificar o endereço básico de DLL, em vez de deixando o sistema operacional realoque as dlls no espaço do processo.  Este parâmetro corresponde a opção \/base \[\] endereço em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`CompanyName`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Company` no assembly.  Para mais informações, consulte a documentação para a opção de `/comp[any]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Configuration`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Configuration` no assembly.  Para mais informações, consulte a documentação para a opção de `/config[uration]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Copyright`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Copyright` no assembly.  Para mais informações, consulte a documentação para a opção de `/copy[right]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Culture`|Parâmetro opcional de `String` .<br /><br /> Especifica a cadeia de caracteres de cultura para associar o assembly.  Para mais informações, consulte a documentação para a opção de `/c[ulture]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`DelaySign`|Parâmetro opcional de `Boolean` .<br /><br /> `true` para colocar somente a chave pública do assembly; `false` para assinar totalmente o assembly.  Para mais informações, consulte a documentação para a opção de `/delay[sign]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Description`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Description` no assembly.  Para mais informações, consulte a documentação para a opção de `/descr[iption]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EmbedResources`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Inserir os recursos especificados na imagem que contém o manifesto do assembly.  Esta tarefa copia o conteúdo do arquivo de recurso na imagem.  Os itens passados para esse parâmetro podem ter os metadados opcionais anexados a eles `LogicalName` chamado e `Access`.  Os metadados de `LogicalName` são usados para especificar o identificador interno para o recurso.  Os metadados de `Access` pode ser definido `private` para tornar o recurso não visível para outros assemblies.  Para mais informações, consulte a documentação para a opção de `/embed[resource]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EvidenceFile`|Parâmetro opcional de `String` .<br /><br /> Insere o arquivo especificado no assembly com o nome de recurso de `Security.Evidence`.<br /><br /> Você não pode usar `Security.Evidence` para recursos normais.  Este parâmetro corresponde à opção de `/e[vidence]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ExitCode`|Parâmetros opcionais somente leitura de saída de `Int32` .<br /><br /> Especifica o código de saída fornecido pelo comando executado.|  
|`FileVersion`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `File Version` no assembly.  Para mais informações, consulte a documentação para a opção de `/fileversion` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Flags`|Parâmetro opcional de `String` .<br /><br /> Especifica um valor para o campo de `Flags` no assembly.  Para mais informações, consulte a documentação para a opção de `/flags` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`GenerateFullPaths`|Parâmetro opcional de `Boolean` .<br /><br /> Faz com que a tarefa usar o caminho absoluto para todos os arquivos que são reportados em uma mensagem de erro.  Este parâmetro corresponde à opção de `/fullpaths` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyContainer`|Parâmetro opcional de `String` .<br /><br /> Especifica um contêiner que contém um par de chaves.  Isso assinará o assembly \(lhe dê um nome forte\) inserindo uma chave pública no manifesto do assembly.  A tarefa assinará no assembly final com a chave particular.  Para mais informações, consulte a documentação para a opção de `/keyn[ame]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyFile`|Parâmetro opcional de `String` .<br /><br /> Especifica um arquivo que contém um par de chaves ou apenas uma chave pública para assinar um assembly.  O compilador insere a chave pública no manifesto do assembly e assina o assembly final com a chave particular.  Para mais informações, consulte a documentação para a opção de `/keyf[ile]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`LinkResources`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Vincula os arquivos de recursos especificados em um assembly.  O recurso torna parte do assembly, mas o arquivo não é copiado.  Os itens passados para esse parâmetro podem ter os metadados opcionais anexados a eles `LogicalName`chamado, `Target`, e `Access`.  Os metadados de `LogicalName` são usados para especificar o identificador interno para o recurso.  Os metadados de `Target` podem especificar o caminho e o nome de arquivo para que a tarefa copia o arquivo, depois do que compila esse novo arquivo do assembly.  Os metadados de `Access` pode ser definido `private` para tornar o recurso não visível para outros assemblies.  Para mais informações, consulte a documentação para a opção de `/link[resource]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`MainEntryPoint`|Parâmetro opcional de `String` .<br /><br /> Especifica o nome totalmente qualificado \(\)*class.method*do método para usar como um ponto de entrada para converter um módulo em um arquivo executável.  Este parâmetro corresponde à opção de `/main` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`OutputAssembly`|Parâmetro de saída de <xref:Microsoft.Build.Framework.ITaskItem> necessário.<br /><br /> Especifica o nome do arquivo gerado por essa tarefa.  Este parâmetro corresponde à opção de `/out` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Platform`|Parâmetro opcional de `String` .<br /><br /> Limites em que a plataforma esse código pode ser executado; deve ser um de `x86`, de `Itanium`, de `x64`, ou de `anycpu`.  O padrão é `anycpu`.  Este parâmetro corresponde à opção de `/platform` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductName`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Product` no assembly.  Para mais informações, consulte a documentação para a opção de `/prod[uct]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductVersion`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `ProductVersion` no assembly.  Para mais informações, consulte a documentação para a opção de `/productv[ersion]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ResponseFiles`|Parâmetro opcional de `String[]` .<br /><br /> Especifica arquivos de resposta que contêm opções adicionais passar pelo vinculador assembly.|  
|`SdkToolsPath`|Parâmetro opcional de `String` .<br /><br /> Especifica o caminho ferramentas SDK, como resgen.exe.|  
|`SourceModules`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Um ou vários módulos a ser compilados em um assembly.  Módulos constarão no manifesto do assembly resultante, e ainda precisarão distribuído e disponível para o assembly carregue.  Os itens passados em este parâmetro podem ter os metadados adicionais chamados `Target`, especificando o caminho e o nome de arquivo para que a tarefa copia o arquivo, depois do que compila esse novo arquivo do assembly.  Para mais informações, consulte a documentação para [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  Este parâmetro corresponde à lista de módulos passados em Al.exe sem uma opção específico.|  
|`TargetType`|Parâmetro opcional de `String` .<br /><br /> Especifica o formato do arquivo de saída: `library` \(biblioteca de códigos\), `exe` \(aplicativo de console\), ou `win` \(aplicativo baseado no Windows\).  O padrão é `library`.  Este parâmetro corresponde à opção de `/t[arget]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`TemplateFile`|Parâmetro opcional de `String` .<br /><br /> Especifica o assembly do qual herdar todos os metadados do assembly, a não ser que o campo de cultura.  O conjunto especificado deve ter um nome forte.<br /><br /> Um assembly que você crie com o parâmetro de `TemplateFile` será um assembly satélite.  Este parâmetro corresponde à opção de `/template` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Timeout`|Parâmetro opcional de `Int32` .<br /><br /> Especifica a quantidade de tempo, em milissegundos, depois do que o executável de tarefa é encerrado.  O valor padrão é `Int.MaxValue`, indicando que não há nenhum intervalo de tempo limite.|  
|`Title`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Title` no assembly.  Para mais informações, consulte a documentação para a opção de `/title` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ToolPath`|Parâmetro opcional de `String` .<br /><br /> Especifica o local de onde a tarefa carregará o arquivo executável subjacente \(Al.exe\).  Se este parâmetro não for especificado, a tarefa usa o caminho de instalação do SDK que corresponde à versão do framework que está executando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Trademark`|Parâmetro opcional de `String` .<br /><br /> Especifica uma cadeia de caracteres para o campo de `Trademark` no assembly.  Para mais informações, consulte a documentação para a opção de `/trade[mark]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Version`|Parâmetro opcional de `String` .<br /><br /> Especifica informações de versão para esse assembly.  O formato de cadeia de caracteres é *principal.menor.compilação.revisão*.  o valor padrão é 0.  Para mais informações, consulte a documentação para a opção de `/v[ersion]` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Icon`|Parâmetro opcional de `String` .<br /><br /> Insere um arquivo .ico no assembly.  O arquivo .ico fornece o arquivo de saída a aparência desejada em Arquivo Explorer.  Este parâmetro corresponde à opção de `/win32icon` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Resource`|Parâmetro opcional de `String` .<br /><br /> Insere um recurso Win32 \(arquivo de .res\) no arquivo de saída.  Para mais informações, consulte a documentação para a opção de `/win32res` em [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
  
## Comentários  
 Além dos parâmetros listados acima, esta tarefa parâmetros herda da classe de <xref:Microsoft.Build.Tasks.ToolTaskExtension> própria, que herda da classe de <xref:Microsoft.Build.Utilities.ToolTask> .  Para obter uma lista de esses parâmetros adicionais e suas descrições, consulte [Classe ToolTaskExtension \(base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir cria um assembly com as opções especificadas.  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)