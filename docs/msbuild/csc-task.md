---
title: "Tarefa Csc | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tarefa Csc [MSBuild]"
  - "MSBuild, tarefa Csc"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa Csc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsula CSC.exe e produz módulos de código (arquivos. netmodule), bibliotecas de vínculo dinâmico (arquivos. dll) ou executáveis (arquivos .exe). Para obter mais informações sobre CSC.exe, consulte [Opções do compilador c#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Csc`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parâmetro `String[]` opcional.<br /><br /> Especifica diretórios adicionais para procurar referências. Para obter mais informações, consulte [/lib (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Parâmetro `String` opcional.<br /><br /> Especifica um ou mais módulos para fazer parte do assembly. Para obter mais informações, consulte [/addmodule (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, compila o código que usa o [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) palavra-chave. Para obter mais informações, consulte [/unsafe (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Parâmetro `String` opcional.<br /><br /> Especifica o arquivo de configuração do aplicativo que contém as configurações de ligação de assembly.|  
|`BaseAddress`|Parâmetro `String` opcional.<br /><br /> Especifica o endereço base preferido no qual carregar uma DLL. O endereço de base padrão para uma DLL é definido pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] common language runtime. Para obter mais informações, consulte [/baseaddress (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Parâmetro `Boolean` opcional.<br /><br /> Especifica se o inteiro aritmético que estoura os limites do tipo de dados faz com que uma exceção em tempo de execução. Para obter mais informações, consulte [/Checked (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Parâmetro `Int32` opcional.<br /><br /> Especifica a página de código a ser usado para todos os arquivos de código fonte na compilação. Para obter mais informações, consulte [/codepage (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Parâmetro `String` opcional.<br /><br /> Especifica o tipo de depuração. `DebugType` pode ser `full` ou `pdbonly`. O padrão é `full`, que permite que um depurador a ser anexado a um programa em execução. Especificando `pdbonly` permite depuração de código quando o programa é iniciado no depurador, mas exibe apenas assembler quando o programa em execução está anexado ao depurador de origem.<br /><br /> Esse parâmetro substitui o `EmitDebugInformation` parâmetro.<br /><br /> Para obter mais informações, consulte [/debug (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Parâmetro `String` opcional.<br /><br /> Define símbolos de pré-processamento. Para obter mais informações, consulte [/define (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, especifica que você deseja que um assembly totalmente assinado. Se `false`, especifica que deseja colocar a chave pública no assembly.<br /><br /> Esse parâmetro não tem nenhum efeito a menos que usado com qualquer um de `KeyFile` ou `KeyContainer` parâmetro.<br /><br /> Para obter mais informações, consulte [/delaysign (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Parâmetro `String` opcional.<br /><br /> Especifica a lista de avisos deve ser desabilitado. Para obter mais informações, consulte [/nowarn (opções do compilador de c#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Parâmetro `String` opcional.<br /><br /> Processa comentários de documentação para um arquivo XML. Para obter mais informações, consulte [/doc (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa gera informações de depuração e o coloca em um arquivo de banco de dados (. PDB) do programa. Se `false`, a tarefa não emite nenhuma informação de depuração. O padrão é `false`. Para obter mais informações, consulte [/debug (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Parâmetro `String` opcional.<br /><br /> Fornece uma maneira conveniente para relatar um erro interno do c# à Microsoft. Esse parâmetro pode ter um valor de `prompt`, `send`, ou `none`. Se o parâmetro for definido como `prompt`, você receberá um prompt quando ocorre um erro interno do compilador. O prompt permite enviar um relatório de erros eletronicamente à Microsoft. Se o parâmetro for definido como `send`, um relatório de erros é enviado automaticamente. Se o parâmetro for definido como `none`, o erro é relatado apenas na saída de texto do compilador. O padrão é `none`. Para obter mais informações, consulte [/errorreport (opções do compilador de c#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Parâmetro `Int32` opcional.<br /><br /> Especifica o tamanho das seções no arquivo de saída. Para obter mais informações, consulte [/filealign (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, especifica o caminho absoluto para o arquivo de saída do compilador. Se `false`, especifica o nome do arquivo. O padrão é `false`. Para obter mais informações, consulte [/fullpaths (opções do compilador de c#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Parâmetro `String` opcional.<br /><br /> Especifica o nome do contêiner de chave criptográfico. Para obter mais informações, consulte [/keycontainer (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Parâmetro `String` opcional.<br /><br /> Especifica o nome do arquivo que contém a chave criptográfica. Para obter mais informações, consulte [/keyfile (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Parâmetro `String` opcional.<br /><br /> Especifica a versão do idioma a ser usado. Para obter mais informações, consulte [/langversion (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Cria um link para um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] recursos no arquivo de saída; o arquivo de recurso não é colocado no arquivo de saída.<br /><br /> Itens passados para esse parâmetro podem ter entradas de metadados opcional chamadas `LogicalName` e `Access`. `LogicalName` corresponde à `identifier` parâmetro o `/linkresource` Alternar, e `Access` corresponde à `accessibility-modifier` parâmetro. Para obter mais informações, consulte [/linkresource (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Parâmetro `String` opcional.<br /><br /> Especifica o local do `Main` método. Para obter mais informações, consulte [/main (opções do compilador de c#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Parâmetro `String` opcional.<br /><br /> Especifica o nome do assembly que este módulo será uma parte.|  
|`NoConfig`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, informa que o compilador não deve compilar com o arquivo CSC. rsp. Para obter mais informações, consulte [/noconfig (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, suprime a exibição de informações de cabeçalho do compilador. Para obter mais informações, consulte [/nologo (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, impede que a importação de mscorlib. dll, que define o namespace do sistema inteiro. Use esse parâmetro se você deseja definir ou criar seus próprios objetos e namespace System. Para obter mais informações, consulte [/nostdlib (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, não inclua o manifesto Win32 padrão.|  
|`Optimize`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, permite otimizações. Se `false`, desabilita otimizações. Para obter mais informações, consulte [/Optimize (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Opcional `String` parâmetro de saída.<br /><br /> Especifica o nome do arquivo de saída. Para obter mais informações, consulte [/out (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Parâmetro `String` opcional.<br /><br /> Especifica o nome de arquivo de informações de depuração. O nome padrão é o nome do arquivo de saída com uma extensão. PDB.|  
|`Platform`|Parâmetro `String` opcional.<br /><br /> Especifica a plataforma do processador sejam direcionadas pelo arquivo de saída. Esse parâmetro pode ter um valor de `x86`, `x64`, ou `anycpu`. O padrão é `anycpu`. Para obter mais informações, consulte [/platform (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Faz com que a tarefa importar informações de tipo público dos itens especificados no projeto atual. Para obter mais informações, consulte [/reference (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Você pode especificar um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] referência alias em um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo adicionando os metadados `Aliases` para o item original de "Referência". Por exemplo, para definir o alias "LS1" na linha de comando a seguir CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> você usaria:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Insere um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] recursos no arquivo de saída.<br /><br /> Itens passados para esse parâmetro podem ter entradas de metadados opcional chamadas `LogicalName` e `Access`. `LogicalName` corresponde à `identifier` parâmetro o `/resource` Alternar, e `Access` corresponde à `accessibility-modifier` parâmetro. Para obter mais informações, consulte [/resource (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Parâmetro `String` opcional.<br /><br /> Especifica o arquivo de resposta que contém comandos para esta tarefa. Para obter mais informações, consulte [@ (especificar arquivo de resposta)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica um ou mais [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] arquivos de origem.|  
|`TargetType`|Parâmetro `String` opcional.<br /><br /> Especifica o formato de arquivo do arquivo de saída. Esse parâmetro pode ter um valor de `library`, que cria uma biblioteca de códigos, `exe`, que cria um aplicativo de console, `module`, que cria um módulo, ou `winexe`, que cria um programa do Windows. O valor padrão é `library`. Para obter mais informações, consulte [/target (opções do compilador de c#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, trata todos os avisos como erros. Para obter mais informações, consulte [/warnaserror (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Parâmetro `Boolean` opcional.<br /><br /> Instrui a tarefa de usar o objeto do compilador em processo, se disponível. Usado somente pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parâmetro `Boolean` opcional.<br /><br /> Registra a saída do compilador usando a codificação UTF-8. Para obter mais informações, consulte [/utf8output (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Parâmetro `Int32` opcional.<br /><br /> Especifica o nível de aviso para o compilador para exibir. Para obter mais informações, consulte [/Warn (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Parâmetro `String` opcional.<br /><br /> Especifica uma lista de avisos a serem tratados como erros. Para obter mais informações, consulte [/warnaserror (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Esse parâmetro substitui o `TreatWarningsAsErrors` parâmetro.|  
|`WarningsNotAsErrors`|Parâmetro `String` opcional.<br /><br /> Especifica uma lista de avisos que não são tratados como erros. Para obter mais informações, consulte [/warnaserror (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Esse parâmetro é útil apenas se o `TreatWarningsAsErrors` parâmetro for definido como `true`.|  
|`Win32Icon`|Parâmetro `String` opcional.<br /><br /> Insere um arquivo. ico no assembly, que fornece o arquivo de saída a aparência desejada no Explorador de arquivos. Para obter mais informações, consulte [/win32icon (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Parâmetro `String` opcional.<br /><br /> Especifica o manifesto Win32 a ser incluído.|  
|`Win32Resource`|Parâmetro `String` opcional.<br /><br /> Insere um arquivo de recurso (. res) do Win32 no arquivo de saída. Para obter mais informações, consulte [/win32res (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros do `Microsoft.Build.Tasks.ManagedCompiler` classe, que herda do <xref:Microsoft.Build.Tasks.ToolTaskExtension> herda de classe, que por si só o <xref:Microsoft.Build.Utilities.ToolTask> classe. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [ToolTaskExtension base de dados de classe](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Csc` tarefa para compilar os arquivos de origem em um executável a `Compile` coleção de itens.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)