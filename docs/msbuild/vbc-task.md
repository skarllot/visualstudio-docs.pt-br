---
title: "Tarefa Vbc | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, tarefa Vbc"
  - "tarefa Vbc [MSBuild]"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa Vbc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Envolve vbc.exe, que gera executáveis \(.exe, as bibliotecas de vínculo dinâmico \(.dll\), ou os módulos de código \(.  netmodule\).  Para obter mais informações sobre vbc.exe, consulte [Compilador de linha de comando do Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros de tarefa de `Vbc` .  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AdditionalLibPaths`|Parâmetro opcional de `String[]` .<br /><br /> Especifica as pastas adicionais para procurar conjuntos especificado no atributo das referências.|  
|`AddModules`|Parâmetro opcional de `String[]` .<br /><br /> Faz com que o compilador torne todas as informações do tipo dos arquivos especificados disponíveis para o projeto que você está compilando atualmente.  Este parâmetro corresponde ao de [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) opção de compilador vbc.exe.|  
|`BaseAddress`|Parâmetro opcional de `String` .<br /><br /> Especifica o endereço básico DLL.  Este parâmetro corresponde ao de [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) opção de compilador vbc.exe.|  
|`CodePage`|Parâmetro opcional de `Int32` .<br /><br /> Especifica a página de código para usar o para todos os arquivos de código\-fonte na compilação.  Este parâmetro corresponde ao de [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) opção de compilador vbc.exe.|  
|`DebugType`|Parâmetro opcional de `String[]` .<br /><br /> Faz com que o compilador gere informações de depuração.  Este parâmetro pode ter os seguintes valores:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> O valor padrão é `full`, que permite que anexar um depurador ao programa em execução.  Um valor de `pdbonly` permite a depuração de código fonte quando o programa é iniciado no depurador, mas o código de linguagem de assembly " exibe somente quando o programa em execução é anexado ao depurador.  Para mais informações, consulte [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Parâmetro opcional de `String[]` .<br /><br /> Define constantes condicionais de compilador.  Os pares do símbolo\/valor são separadas por ponto\-e\-vírgula e especificados com a seguinte sintaxe:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *valor2*<br /><br /> Este parâmetro corresponde ao de [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) opção de compilador vbc.exe.|  
|`DelaySign`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, a tarefa colocar a chave pública do assembly.  Se `false`, a tarefa assinar totalmente o assembly.  o valor padrão é `false`. Este parâmetro não tem efeito a menos que usado com o parâmetro de `KeyFile` ou o parâmetro de `KeyContainer` .  Este parâmetro corresponde ao de [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) opção de compilador vbc.exe.|  
|`DisabledWarnings`|Parâmetro opcional de `String` .<br /><br /> Suprime os avisos específicos.  Você só precisa especificar a parte numérica do identificador de aviso.  Vários avisos são separadas por ponto\-e\-vírgula.  Este parâmetro corresponde ao de [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) opção de compilador vbc.exe.|  
|`DocumentationFile`|Parâmetro opcional de `String` .<br /><br /> Processa os comentários de documentação para o arquivo XML especificado.  Este parâmetro substitui o atributo de `GenerateDocumentation` .  Para obter mais informações, consulte [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, a tarefa gerar informações de depuração e o coloca em um arquivo de .pdb.  Para mais informações, consulte [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Parâmetro opcional de `String` .<br /><br /> Especifica como a tarefa deve relatar erros do compilador interno.  Este parâmetro pode ter os seguintes valores:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Se `prompt` é especificado e ocorrer um erro interno do compilador, o usuário é apresentada uma opção de wheter enviar os dados de erro à Microsoft.<br /><br /> Se `send` é especificado e ocorrer um erro interno do compilador, a tarefa envia os dados de erro à Microsoft.<br /><br /> O valor padrão é `none`, que analisam erros na saída de somente texto.<br /><br /> Este parâmetro corresponde ao de [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) opção de compilador vbc.exe.|  
|`FileAlignment`|Parâmetro opcional de `Int32` .<br /><br /> Especifica, em bytes, onde alinhar as seções do arquivo de saída.  Este parâmetro pode ter os seguintes valores:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Este parâmetro corresponde ao de [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) opção de compilador vbc.exe.|  
|`GenerateDocumentation`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, gera informações da documentação e colocados em um arquivo XML com o nome do arquivo executável ou biblioteca que a tarefa está criando.  Para obter mais informações, consulte [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Importa namespaces das coleções específicas de item.  Este parâmetro corresponde ao de [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) opção de compilador vbc.exe.|  
|`KeyContainer`|Parâmetro opcional de `String` .<br /><br /> Especifica o nome do contêiner de chave de criptografia.  Corresonds de esse parâmetro de [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) a opção de compilador vbc.exe.|  
|`KeyFile`|Parâmetro opcional de `String` .<br /><br /> Especifica o nome de arquivo que contém a chave de criptografia.  Para obter mais informações, consulte [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Parâmetro opcional de [String](assetId:///String?qualifyHint=False&autoUpgrade=True) .<br /><br /> Especifica a versão da linguagem, “9 " ou “10 ".|  
|`LinkResources`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Criar um link a um recurso do .NET Framework no arquivo de saída; o arquivo de recursos não é colocado no arquivo de saída.  Este parâmetro corresponde ao de [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) opção de compilador vbc.exe.|  
|`MainEntryPoint`|Parâmetro opcional de `String` .<br /><br /> Especifica a classe ou módulo que contém o procedimento `Sub Main`.  Corresonds de esse parâmetro de [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) a opção de compilador vbc.exe.|  
|`ModuleAssemblyName`|Parâmetro opcional de `String` .<br /><br /> Especifica o assembly que este módulo é uma parte.|  
|`NoConfig`|Parâmetro opcional de `Boolean` .<br /><br /> Especifica que o compilador não deve usar o arquivo vbc.rsp.  Este parâmetro corresponde ao parâmetro de [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) de compilador vbc.exe.|  
|`NoLogo`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, suprime a exibição das informações de cabeçalho de compilador.  Este parâmetro corresponde ao de [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) opção de compilador vbc.exe.|  
|`NoStandardLib`|Parâmetro opcional de `Boolean` .<br /><br /> Faz com que o compilador não referencie as bibliotecas padrão.  Este parâmetro corresponde ao de [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) opção de compilador vbc.exe.|  
|`NoVBRuntimeReference`|Parâmetro opcional de `Boolean` .<br /><br /> Uso interno somente.  Se verdadeiro, a referência automática a Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, a tarefa suprime todos os avisos.  Para obter mais informações, consulte [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, ativar otimizações de compilador.  Este parâmetro corresponde ao de [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) opção de compilador vbc.exe.|  
|`OptionCompare`|Parâmetro opcional de `String` .<br /><br /> Especifica como são feitas comparações de cadeias de caracteres.  Este parâmetro pode ter os seguintes valores:<br /><br /> -   `binary`<br />-   `text`<br /><br /> O valor `binary` especifica que a tarefa usa comparações binárias de cadeias de caracteres.  O valor `text` especifica que a tarefa usa comparações de cadeias de caracteres de texto.  O valor padrão de esse parâmetro é `binary`.  Este parâmetro corresponde ao de [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) opção de compilador vbc.exe.|  
|`OptionExplicit`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`declaração explícita de variáveis, é necessário.  Este parâmetro corresponde ao de [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) opção de compilador vbc.exe.|  
|`OptionInfer`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, permite inferência de tipos de variáveis.|  
|`OptionStrict`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, a tarefa aplica semânticas de tipo rígidas para restringir conversões implícitas de tipo.  Este parâmetro corresponde ao de [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) opção de compilador vbc.exe.|  
|`OptionStrictType`|Parâmetro opcional de `String` .<br /><br /> Especifica que a semântica de tipo rígidas gera um aviso.  Atualmente, somente “custom” é suportado.  Este parâmetro corresponde ao de [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) opção de compilador vbc.exe.|  
|`OutputAssembly`|Parâmetro de saída de `String` opcional.<br /><br /> Especifica o nome do arquivo de saída.  Este parâmetro corresponde ao de [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) opção de compilador vbc.exe.|  
|`Platform`|Parâmetro opcional de `String` .<br /><br /> Especifica a plataforma do processador a ser destinada pelo arquivo de saída.  Este parâmetro pode ter um valor de `x86`, de `x64`, de `Itanium`, ou de `anycpu`.  O padrão é `anycpu`.  Este parâmetro corresponde ao de [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) opção de compilador vbc.exe.|  
|`References`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Faz com que a tarefa importar informações pública do tipo dos itens especificados no projeto atual.  Este parâmetro corresponde ao de [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) opção de compilador vbc.exe.|  
|`RemoveIntegerChecks`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, verificações de erro de estouro de inteiros desativa.  o valor padrão é `false`.  Este parâmetro corresponde ao de [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) opção de compilador vbc.exe.|  
|`Resources`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Insere um recurso do .NET Framework no arquivo de saída.  Este parâmetro corresponde ao de [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) opção de compilador vbc.exe.|  
|`ResponseFiles`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica o arquivo de resposta que contém comandos para esta tarefa.  Este parâmetro corresponde à opção de [@ \(especificar Arquivo de resposta\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) de compilador vbc.exe.|  
|`RootNamespace`|Parâmetro opcional de `String` .<br /><br /> Especifica o namespace raiz para todas as declarações de tipo.  Este parâmetro corresponde ao de [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) opção de compilador vbc.exe.|  
|`SdkPath`|Parâmetro opcional de `String` .<br /><br /> Especifica o local mscorlib.dll e microsoft.visualbasic.dll.  Este parâmetro corresponde ao de [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) opção de compilador vbc.exe.|  
|`Sources`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica um ou mais arquivos de origem de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .|  
|`TargetCompactFramework`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, a tarefa tem como alvo [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  Este interruptor corresponde ao de [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) opção de compilador vbc.exe.|  
|`TargetType`|Parâmetro opcional de `String` .<br /><br /> Especifica o formato do arquivo de saída.  Este parâmetro pode ter um valor de `library`, que cria uma biblioteca de códigos, `exe`, que cria um aplicativo de console, `module`, que cria um módulo, ou `winexe`, que cria um programa do windows.  O padrão é `library`.  Este parâmetro corresponde ao de [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) opção de compilador vbc.exe.|  
|`Timeout`|Parâmetro opcional de `Int32` .<br /><br /> Especifica a quantidade de tempo, em milissegundos, depois do que o executável de tarefa é encerrado.  O valor padrão é `Int.MaxValue`, indicando que não há nenhum intervalo de tempo limite.|  
|`ToolPath`|Parâmetro opcional de `String` .<br /><br /> Especifica o local de onde a tarefa carregará o arquivo executável subjacente \(vbc.exe\).  Se este parâmetro não for especificado, a tarefa usa o caminho de instalação do SDK que corresponde à versão do framework que está executando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, todos os avisos é tratado como erros.  Para mais informações, consulte [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Parâmetro opcional de `Boolean` .<br /><br /> Instrui a tarefa usar o objeto para processo de compilador, se disponível.  Usado somente por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parâmetro opcional de `Boolean` .<br /><br /> Efetua logon saída do compilador usando a codificação UTF\-8.  Este parâmetro corresponde ao de [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) opção de compilador vbc.exe.|  
|`Verbosity`|Parâmetro opcional de `String` .<br /><br /> Especifica a verbosidade de saída do compilador.  A verbosidade pode ser `Quiet`, `Normal` \(o padrão\), ou `Verbose`.|  
|`WarningsAsErrors`|Parâmetro opcional de `String` .<br /><br /> Especifica uma lista de tratar avisos como erros.  Para mais informações, consulte [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Este parâmetro substitui o parâmetro de `TreatWarningsAsErrors` .|  
|`WarningsNotAsErrors`|Parâmetro opcional de `String` .<br /><br /> Especifica uma lista de avisos que não são tratados como erros.  Para mais informações, consulte [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Esse parâmetro é útil somente se o parâmetro de `TreatWarningsAsErrors` é definido como `true`.|  
|`Win32Icon`|Parâmetro opcional de `String` .<br /><br /> Insere um arquivo .ico no assembly, que fornece o arquivo de saída a aparência desejada em Arquivo Explorer.  Este parâmetro corresponde ao de [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) opção de compilador vbc.exe.|  
|`Win32Resources`|Parâmetro opcional de `String` .<br /><br /> Insere um arquivo de recurso Win32 \(.res\) no arquivo de saída.  Este parâmetro corresponde ao de [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) opção de compilador vbc.exe.|  
  
## Comentários  
 Além dos parâmetros listados acima, esta tarefa parâmetros herda da classe de <xref:Microsoft.Build.Tasks.ToolTaskExtension> própria, que herda da classe de <xref:Microsoft.Build.Utilities.ToolTask> .  Para obter uma lista de esses parâmetros adicionais e suas descrições, consulte [Classe ToolTaskExtension \(base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Exemplo  
 O seguinte exemplo cria um projeto de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)