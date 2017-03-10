---
title: "Propriedades de projeto comuns do MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Propriedade ExcludeDeploymentUrl"
  - "msbuild, propriedades comuns"
  - "msbuild, propriedades de arquivo de projeto"
  - "propriedades de arquivo de projeto (MSBuild)"
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
caps.latest.revision: 36
caps.handback.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Propriedades de projeto comuns do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A tabela a seguir lista frequentemente usadas propriedades que são definidas nos arquivos de projeto do Visual Studio ou incluído nos arquivos. targets que o MSBuild fornece.  
  
 Arquivos de projeto no Visual Studio \(. csproj,. vbproj, vcxproj e outros\) contêm código de XML do MSBuild que é executado quando você cria um projeto usando o IDE.  Projetos normalmente importem um ou mais arquivos. targets para definir o processo de criação.  Para obter mais informações, consulte [Arquivos .Targets](../msbuild/msbuild-dot-targets-files.md).  
  
## Lista de Propriedades Comuns e Parâmetros  
  
|Propriedade ou o nome do parâmetro|Descrição|  
|----------------------------------------|---------------|  
|AdditionalLibPaths|Especifica as pastas adicionais no qual os compiladores devem procurar assemblies de referência.|  
|AddModules|Faz com que o compilador verifique todos os tipos de arquivos disponíveis para o projeto que você está compilando informações especificado.  Esta propriedade é equivalente de `/addModules` comutador de compilador.|  
|ALToolPath|O caminho onde AL.exe pode ser encontrado.  Essa propriedade substitui a versão atual do AL.exe para habilitar o uso de uma versão diferente.|  
|ApplicationIcon|O arquivo de ícone. ico para passar para o compilador para inserir como um ícone de Win32.  A propriedade é equivalente de `/win32icon` comutador de compilador.|  
|ApplicationManifest|Especifica o caminho do arquivo que é usado para gerar informações de manifesto externas User Account Control \(UAC\).  Aplica\-se somente a projetos do Visual Studio destinado [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> Na maioria dos casos, o manifesto é incorporado.  No entanto, se você usar registro gratuito COM ou [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, o manifesto pode ser um arquivo externo que é instalado junto com seus assemblies de aplicativo.  Para obter mais informações, consulte a propriedade NoWin32Manifest neste tópico.|  
|AssemblyOriginatorKeyFile|Especifica o arquivo que é usado para assinar o assembly \(. snk ou. pfx\) e que é passado para o [Tarefa ResolveKeySource](../msbuild/resolvekeysource-task.md) para gerar a chave real que é usada para assinar o assembly.|  
|AssemblySearchPaths|Uma lista de locais para pesquisa durante a resolução de assembly de referência em tempo de compilação.  A ordem na qual os caminhos aparecem nesta lista é significativa porque caminhos listados anteriormente tem precedência sobre entradas posteriores.|  
|AssemblyName|O nome do assembly de saída final depois que o projeto é criado.|  
|BaseAddress|Especifica o endereço base do assembly de saída principal.  Esta propriedade é equivalente de `/baseaddress` comutador de compilador.|  
|BaseOutputPath|Especifica o caminho base para o arquivo de saída.  Se estiver definido, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usará `OutputPath = $(BaseOutputPath)\$(Configuration)\`.  Exemplo de sintaxe: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|A pasta de nível superior onde todas as pastas de saída intermediária específicos da configuração são criadas.  O valor padrão é `obj\`.  O código a seguir é um exemplo: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Um valor booleano que indica se as referências do projeto são criadas ou excluídas em paralelo quando Proc múltiplo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] é usado.  O valor padrão é `true`, que significa que projetos serão compilados em paralelo se o sistema tiver vários processadores ou núcleos.|  
|BuildProjectReferences|Um valor booleano que indica se as referências de projeto são criadas por [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Definir `false` se você estiver criando o seu projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\), `true` se contrário.|  
|CleanFile|O nome do arquivo que será usado como o "cache limpo". Limpar cache é uma lista dos arquivos gerados sejam excluídos durante a operação de limpeza.  O arquivo é colocado no caminho de saída intermediária pelo processo de compilação.<br /><br /> Esta propriedade especifica apenas os nomes de arquivo que não possuem informações de caminho.|  
|Página de código|Especifica a página de código a ser usado para todos os arquivos de código\-fonte na compilação.  Esta propriedade é equivalente de `/codepage` comutador de compilador.|  
|CompilerResponseFile|Um arquivo de resposta opcional que pode ser passado para as tarefas do compilador.|  
|Configuração|A configuração que você está criando, "Debug" ou "Versão".|  
|CscToolPath|O caminho do csc.exe, o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] compilador.|  
|CustomBeforeMicrosoftCommonTargets|O nome de um arquivo de projeto ou arquivo de destinos que deve ser importados automaticamente antes da importação de destinos comuns.|  
|DebugSymbols|Um valor booliano que indica se os símbolos são gerados pela compilação.<br /><br /> Definindo **\/p:DebugSymbols\=false** na linha de comando desabilita a geração de arquivos de símbolo \(. PDB\) de banco de dados de programa.|  
|DefineConstants|Define as constantes de compilador condicional.  Pares de símbolo\/valor separados por ponto e vírgula e são especificadas usando a sintaxe a seguir:<br /><br /> *symbol1 \= value1; symbol2 \= valor2*<br /><br /> A propriedade é equivalente de `/define` comutador de compilador.|  
|DefineDebug|Um valor booliano que indica se você deseja que a constante de depuração definida.|  
|DefineTrace|Um valor booliano que indica se você deseja que a constante de rastreamento definida.|  
|Tipo\_de\_depuração|Define o nível de informações de depuração que você deseja que seja gerado.  Os valores válidos são "total", "somente pdb" e "none".|  
|DelaySign|Um valor booliano que indica se você deseja atrasar a assinatura do assembly em vez de sinal completo\-lo.|  
|DisabledWarnings|Suprime os avisos especificados.  Somente a parte numérica do identificador de aviso deve ser especificada.  Vários avisos são separados por ponto e vírgula.  Esse parâmetro corresponde do `/nowarn` opção do compilador vbc.exe.|  
|DisableFastUpToDateCheck|Um valor booleano que se aplica a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apenas.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] criar manager usa um processo chamado FastUpToDateCheck para determinar se um projeto deve ser reconstruído para ser atualizado.  Esse processo é mais rápido que usar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para determinar isso.  Definindo a propriedade DisableFastUpToDateCheck como `true` permite ignorar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] criar gerenciador e forçá\-lo a usar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para determinar se o projeto é atualizado.|  
|DocumentationFile|O nome do arquivo que é gerado como o arquivo de documentação XML.  Esse nome inclui o nome de arquivo e não tem nenhuma informação de caminho.|  
|ErrorReport|Especifica como a tarefa de compilador deve relatar erros do compilador interno.  Os valores válidos são "prompts", "Enviar" ou "none". Esta propriedade é equivalente de `/errorreport` comutador de compilador.|  
|ExcludeDeploymentUrl|O [Tarefa GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) adiciona uma marca deploymentProvider no manifesto de implantação se o arquivo de projeto inclui qualquer um dos seguintes elementos:<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> Usando ExcludeDeploymentUrl, no entanto, você pode impedir que a marca deploymentProvider que está sendo adicionado ao manifesto de implantação, mesmo se qualquer uma das URLs anteriores forem especificados. Para fazer isso, adicione a propriedade a seguir ao arquivo de projeto:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` **Note:**  ExcludeDeploymentUrl não é exposta na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE e pode ser definida apenas editando manualmente o arquivo de projeto. A definição dessa propriedade não afeta a publicação no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; ou seja, a marca deploymentProvider ainda será adicionada para a URL especificada pelo PublishUrl.|  
|FileAlignment|Especifica, em bytes, onde alinhar as seções do arquivo de saída.  Os valores válidos são 512, 1024, 2048, 4096, 8192.  Esta propriedade é equivalente de `/filealignment` comutador de compilador.|  
|FrameworkPathOverride|Especifica o local de mscorlib. dll e microsoft.visualbasic.dll.  Este parâmetro é equivalente do `/sdkpath` opção do compilador vbc.exe.|  
|GenerateDocumentation|Um parâmetro booleano que indica se a documentação é gerada pela compilação.  Se `true`, a compilação gera informações sobre a documentação e o coloca em um arquivo. XML, junto com o nome do arquivo executável ou biblioteca que criou a tarefa de compilação.|  
|IntermediateOutputPath|O caminho de saída completo intermediários conforme derivado de `BaseIntermediateOutputPath`, se nenhum caminho for especificado.  Por exemplo, \\obj\\debug\\.  Se essa propriedade for substituída, definindo `BaseIntermediateOutputPath` não tem nenhum efeito.|  
|KeyContainerName|O nome do contêiner de chave de nome forte.|  
|KeyOriginatorFile|O nome do arquivo de chave de nome forte.|  
|NoWin32Manifest|Determina se o compilador gera o manifesto Win32 padrão no assembly de saída.  O valor padrão de `false` significa que o manifesto Win32 padrão é gerado para todos os aplicativos.  Esta propriedade é equivalente de `/nowin32manifest` comutador de compilador de vbc.exe.|  
|\/Moduleassemblyname|O nome do assembly que o módulo compilado deve ser incorporado.  A propriedade é equivalente de `/moduleassemblyname` comutador de compilador.|  
|\/Nologo|Um valor booliano que indica se você deseja que o logotipo do compilador para ser desligado.  Esta propriedade é equivalente de `/nologo` comutador de compilador.|  
|\/Nostdlib|Um valor booliano que indica se deve evitar fazem referência à biblioteca padrão \(mscorlib. dll\).  O valor padrão é `false`.|  
|NoVBRuntimeReference|Um valor booleano que indica se o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tempo de execução \(Microsoft.VisualBasic.dll\) deve ser incluído como uma referência no projeto.|  
|NoWin32Manifest|Um valor booleano que indica se as informações do manifesto do controle de conta de usuário \(UAC\) serão incorporadas no aplicativo executável da.  Aplica\-se somente a projetos do Visual Studio destinado [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  Em projetos implantados usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM sem registro, esse elemento será ignorado. `False` \(o valor padrão\) Especifica que as informações do manifesto do controle de conta de usuário \(UAC\) ser incorporado no executável do aplicativo.  `True` Especifica que as informações de manifesto UAC não ser inserido.<br /><br /> Essa propriedade só se aplica ao [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projetos direcionamento [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  Em projetos implantados usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM sem registro, essa propriedade é ignorada.<br /><br /> Você deve adicionar NoWin32Manifest somente se você não quiser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para qualquer manifesto incorporado no aplicativo do executável; esse processo é chamado *virtualização*.  Para usar a virtualização, definir `<ApplicationManifest>` em conjunto com `<NoWin32Manifest>` da seguinte maneira:<br /><br /> -   Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos, remova o `<ApplicationManifest>` nó.  \(No [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos, `<NoWin32Manifest>` é ignorado quando uma `<ApplicationManifest>` nó existe.\)<br />-   Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projetos, defina `<ApplicationManifest>` para `False` e `<NoWin32Manifest>` para `True`.  \(No [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projetos, `<ApplicationManifest>` substitui `<NoWin32Manifest>`.\)|  
|Otimizar|Um valor booleano que quando definido como `true`, permite otimizações do compilador.  Esta propriedade é equivalente de `/optimize` comutador de compilador.|  
|\/Optioncompare|Especifica como são feitas comparações de cadeia de caracteres.  Os valores válidos são "binary" ou "text". Esta propriedade é equivalente de `/optioncompare` comutador de compilador de vbc.exe.|  
|\/Optionexplicit|Um valor booleano que quando definido como `true`, exige a declaração explícita de variáveis no código\-fonte.  Esta propriedade é equivalente de `/optionexplicit` comutador de compilador.|  
|OptionInfer|Um valor booleano que quando definido como `true`, permite inferência de tipos de variáveis.  Esta propriedade é equivalente de `/optioninfer` comutador de compilador.|  
|OptionStrict|Um valor booleano que quando definido como `true`, faz com que a tarefa de compilação para impor semânticas de tipo rígidas para restringir a conversões de tipo implícito.  Esta propriedade é equivalente de `/optionstrict` opção do compilador vbc.exe.|  
|OutputPath|Especifica o caminho para o diretório de saída, relativo ao diretório do projeto, por exemplo, "bin".|  
|OutputType|Especifica o formato de arquivo do arquivo de saída.  Este parâmetro pode ter um dos seguintes valores:<br /><br /> -   Biblioteca.  Cria uma biblioteca de códigos.  \(Valor padrão\).<br />-   Exe.  Cria um aplicativo de console.<br />-   Módulo.  Cria um módulo.<br />-   Winexe.  Cria um programa baseado em Windows.<br /><br /> Esta propriedade é equivalente de `/target` opção do compilador vbc.exe.|  
|OverwriteReadOnlyFiles|Um valor booliano que indica se você deseja habilitar a compilação substituir os arquivos somente leitura ou acionar um erro.|  
|PdbFile|O nome do arquivo do arquivo. PDB que estão emitindo.  Esta propriedade é equivalente de `/pdb` opção do compilador csc.exe.|  
|Plataforma|O sistema operacional que você estiver criando para.  Os valores válidos são "Qualquer CPU", "x86" e "x64".|  
|RemoveIntegerChecks|Um valor booliano que indica se deve desabilitar a verificação de erro de estouro de inteiro.  O valor padrão é `false`.  Esta propriedade é equivalente de `/removeintchecks` opção do compilador vbc.exe.|  
|SGenUseProxyTypes|Um valor booliano que indica se os tipos de proxy devem ser gerados por SGen.exe.<br /><br /> O destino SGen usa essa propriedade para definir o sinalizador UseProxyTypes.  Essa propriedade assume true como padrão e não há nenhuma interface do usuário para alterar isso.  Para gerar o assembly de serialização para tipos não webservice, adicione essa propriedade ao arquivo de projeto e defini\-lo como false antes de importar o Microsoft.Common.Targets ou o C\#\/VB.targets.|  
|SGenToolPath|Um caminho de ferramenta opcional que indica onde obter SGen.exe quando a versão atual do SGen.exe é substituída.|  
|StartupObject|Especifica a classe ou módulo que contém o método Main ou o procedimento Sub Main.  Esta propriedade é equivalente de `/main` comutador de compilador.|  
|ProcessorArchitecture|A arquitetura do processador é usada quando as referências de assembly são resolvidas.  Os valores válidos são "msil", "x 86", "amd64" ou "ia64".|  
|RootNamespace|O namespace raiz para usar ao nomear um recurso incorporado.  Este namespace é parte do nome de manifesto do recurso inserido.|  
|Satellite\_AlgorithmId|A identificação do algoritmo de hash AL.exe usar quando os assemblies satélite são criados.|  
|Satellite\_BaseAddress|O endereço base para usar ao assemblies satélites específicas de cultura são criados usando o `CreateSatelliteAssemblies` destino.|  
|Satellite\_CompanyName|O nome da empresa para passar para AL.exe durante a geração do assembly satélite.|  
|Satellite\_Configuration|O nome da configuração de passar para AL.exe durante a geração do assembly satélite.|  
|Satellite\_Description|O texto de descrição para passar para AL.exe durante a geração do assembly satélite.|  
|Satellite\_EvidenceFile|Incorpora o arquivo especificado no assembly satélite que tem o nome do recurso "Evidence."|  
|Satellite\_FileVersion|Especifica uma cadeia de caracteres para o campo de versão do arquivo no assembly satélite.|  
|Satellite\_Flags|Especifica um valor para o campo de sinalizadores no assembly satélite.|  
|Satellite\_GenerateFullPaths|Faz com que a tarefa de compilação usar caminhos absolutos para arquivos relatados em uma mensagem de erro.|  
|Satellite\_LinkResource|Vincula os arquivos de recurso especificado para um assembly satélite.|  
|Satellite\_MainEntryPoint|Especifica o nome totalmente qualificado \(ou seja, class.method\) do método a ser usado como um ponto de entrada quando um módulo é convertido em um arquivo executável durante a geração do assembly satélite.|  
|Satellite\_ProductName|Especifica uma cadeia de caracteres para o campo Product no assembly satélite.|  
|Satellite\_ProductVersion|Especifica uma cadeia de caracteres do campo ProductVersion no assembly satélite.|  
|Satellite\_TargetType|Especifica o formato de arquivo do arquivo de saída do assembly satélite como "biblioteca", "exe" ou "win." O valor padrão é a "biblioteca".|  
|Satellite\_Title|Especifica uma cadeia de caracteres para o campo título no assembly satélite.|  
|Satellite\_Trademark|Especifica uma cadeia de caracteres para o campo de marca registrada no assembly satélite.|  
|Satellite\_Version|Especifica as informações de versão do assembly satélite.|  
|Satellite\_Win32Icon|Insere um arquivo de ícone. ico no assembly satélite.|  
|Satellite\_Win32Resource|Insere um recurso do Win32 \(arquivo. res\) no assembly satélite.|  
|SubsystemVersion|Especifica a versão mínima do subsistema que pode usar o arquivo executável gerado.  Esta propriedade é equivalente de `/subsystemversion` comutador de compilador.  Para obter informações sobre o valor padrão desta propriedade, consulte [\/subsystemversion](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) ou [\/subsystemversion \(Specify minimum subsystem version\)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option).|  
|TargetCompactFramework|A versão do .NET Compact Framework que é necessário para executar o aplicativo que você está criando.  Especificar isso, você poderá fazer referência a determinados assemblies do framework que você não poderá fazer referência a outra forma.|  
|TargetFrameworkVersion|A versão dos [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que é necessário para executar o aplicativo que você está criando.  Especificar isso, você poderá fazer referência a determinados assemblies do framework que você não poderá fazer referência a outra forma.|  
|TreatWarningsAsErrors|Um parâmetro booleano que, se `true`, faz com que todos os avisos sejam tratados como erros.  Este parâmetro é equivalente do `/nowarn` comutador de compilador.|  
|UseHostCompilerIfAvailable|Um parâmetro booleano que, se `true`, faz com que a tarefa de compilação usar o objeto do compilador em processo, se ele estiver disponível.  Esse parâmetro é usado somente pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|Utf8Output|Um parâmetro booleano que, se `true`, registra a saída do compilador usando a codificação UTF\-8.  Este parâmetro é equivalente do `/utf8Output` comutador de compilador.|  
|VbcToolPath|Um caminho opcional que indica a outro local para vbc.exe quando a versão atual do vbc.exe é substituída.|  
|VbcVerbosity|Especifica a verbosidade do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] de saída do compilador.  Os valores válidos são "Silencioso", "Normal" \(o valor padrão\) ou "Detalhado".|  
|VisualStudioVersion|Especifica a versão do Visual Studio sob a qual este projeto deve ser considerado para estar em execução.  Se esta propriedade não for especificada, o MSBuild a define como um valor padrão razoáveis.<br /><br /> Essa propriedade é usada em vários tipos de projetos para especificar o conjunto de destinos que são usados para a compilação.  Se `ToolsVersion` for definido como 4.0 ou superior para um projeto, `VisualStudioVersion` é usado para especificar o subconjunto de ferramentas para usar.  Para obter mais informações, consulte [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Especifica uma lista de avisos a serem tratados como erros.  Este parâmetro é equivalente do `/warnaserror` comutador de compilador.|  
|WarningsNotAsErrors|Especifica uma lista de avisos que não são tratados como erros.  Este parâmetro é equivalente do `/warnaserror` comutador de compilador.|  
|Win32Manifest|O nome do arquivo de manifesto deve ser incorporado no assembly final.  Este parâmetro é equivalente do `/win32Manifest` comutador de compilador.|  
|Win32Resource|O nome do arquivo de recurso Win32 a ser inserido no assembly final.  Este parâmetro é equivalente do `/win32resource` comutador de compilador.|  
  
## Consulte também  
 [Itens de projeto comuns do MSBuild](../msbuild/common-msbuild-project-items.md)