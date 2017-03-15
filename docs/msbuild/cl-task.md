---
title: Tarefa CL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 18
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4ad346483c37e1f221ebd396a60d30b5bf94a028

---
# <a name="cl-task"></a>Tarefa CL
Encapsula a ferramenta do compilador Visual C++, cl.exe. O compilador produz arquivos executáveis (.exe), arquivos de biblioteca de vínculo dinâmico (.dll) ou arquivos de módulo de código (.netmodule). Para obter mais informações, consulte [Opções do compilador](/visual-cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **CL**. A maioria dos parâmetros de tarefa e alguns conjuntos de parâmetros correspondem a uma opção de linha de comando.  
  
-   **AdditionalIncludeDirectories**  
  
     Parâmetro String[] opcional.  
  
     Adiciona um diretório à lista de diretórios que são pesquisados para arquivos de inclusão.  
  
     Para obter mais informações, consulte [/I (diretórios de inclusão adicionais)](/visual-cpp/build/reference/i-additional-include-directories).  
  
-   **AdditionalOptions**  
  
     Parâmetro String opcional.  
  
     Uma lista de opções de linha de comando. Por exemplo, "/*option1* /*option2* /*option#*". Use esse parâmetro para especificar opções de linha de comando não representadas por nenhum outro parâmetro da tarefa.  
  
     Para obter mais informações, consulte [Opções do compilador](/visual-cpp/build/reference/compiler-options).  
  
-   Parâmetro **AdditionalUsingDirectories**Optional String[].  
  
     Especifica um diretório em que o compilador pesquisará para resolver referências de arquivo passadas para diretiva **#using**.  
  
     Para obter mais informações, consulte [/AI (Especificar Diretórios de Metadados)](/visual-cpp/build/reference/ai-specify-metadata-directories).  
  
-   **AlwaysAppend**  
  
     Parâmetro String opcional.  
  
     Uma cadeia de caracteres sempre é emitida na linha de comando. Seu valor padrão é "**/c**".  
  
-   **AssemblerListingLocation**  
  
     Cria um arquivo de listagem que contém o código do assembly.  
  
     Para obter mais informações, consulte a opção **/Fa** em [/FA, /Fa (Arquivo de Listagem)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **AssemblerOutput**  
  
     Parâmetro String opcional.  
  
     Cria um arquivo de listagem que contém o código do assembly.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **NoListing** - *\<none>*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **AssemblyAndSourceCode** - **/FAs**  
  
    -   **All** - **/FAcs**  
  
     Para obter mais informações, consulte as opções **/FA**, **/FAc**, **/FAs** e **/FAcs** opções em [/FA, /Fa (Arquivo de Listagem)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **BasicRuntimeChecks**  
  
     Parâmetro String opcional.  
  
     Habilita e desabilita o recurso de verificações de erro em tempo de execução, em conjunto com o pragma [runtime_checks](/visual-cpp/preprocessor/runtime-checks).  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Default** -                          *\<none>*  
  
    -   **StackFrameRuntimeCheck** - **/RTCs**  
  
    -   **UninitializedLocalUsageCheck** - **/RTCu**  
  
    -   **EnableFastChecks** -                          **/RTC1**  
  
     Para obter mais informações, consulte [/RTC (verificações de erro em tempo de execução)](/visual-cpp/build/reference/rtc-run-time-error-checks).  
  
-   **BrowseInformation**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, criará um arquivo de informações de procura.  
  
     Para obter mais informações, consulte a opção **/FR** em [/FR, /Fr (criar Arquivo .Sbr)](/visual-cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BrowseInformationFile**  
  
     Parâmetro String opcional.  
  
     Especifica um nome de arquivo para o arquivo de informações de procura.  
  
     Para obter mais informações, consulte o parâmetro **BrowseInformation** nessa tabela e também consulte [/FR, /Fr (criar Arquivo .Sbr)](/visual-cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BufferSecurityCheck**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, detectará alguns estouros de buffer que substituem o endereço de retorno, uma técnica comum para explorar o código que não impõe restrições de tamanho do buffer.  
  
     Para obter mais informações, consulte [/GS (verificação de segurança do buffer)](/visual-cpp/build/reference/gs-buffer-security-check).  
  
-   **BuildingInIDE**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, indicará que **MSBuild** é invocado pelo IDE. Caso contrário, **MSBuild** será invocado na linha de comando.  
  
-   **CallingConvention**  
  
     Parâmetro String opcional.  
  
     Especifica a convenção de chamada, que determina a ordem na qual os argumentos de função são colocados na pilha, se a função do chamador ou a função chamada remove os argumentos da pilha no final da chamada e a convenção de decoração de nome que o compilador usa para identificar funções individuais.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Cdecl** - **/Gd**  
  
    -   **FastCall** -                          **/Gr**  
  
    -   **StdCall** -                          **/Gz**  
  
     Para obter mais informações, consulte [/Gd, /Gr, /Gv, /Gz (convenção de chamada)](/visual-cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
-   **CompileAs**  
  
     Parâmetro String opcional.  
  
     Especifica se o arquivo de entrada deve ser compilado como um arquivo de origem C ou C++.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Default** - *\<none>*  
  
    -   **CompileAsC** - **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     Para obter mais informações, consulte [/Tc, /Tp, /TC, /TP (especificar o tipo de arquivo de origem)](/visual-cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
-   **CompileAsManaged**  
  
     Parâmetro String opcional.  
  
     Permite que aplicativos e componentes usem recursos do CLR (Common Language Runtime).  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **false** - *\<none>*  
  
    -   **true** - **/clr**  
  
    -   **Pure** - **/clr:pure**  
  
    -   **Safe** - **/clr:safe**  
  
    -   **OldSyntax** - **/clr:oldSyntax**  
  
     Para obter mais informações, consulte [/clr (compilação de Common Language Runtime)](/visual-cpp/build/reference/clr-common-language-runtime-compilation).  
  
-   **CreateHotpatchableImage**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, informará ao compilador para preparar uma imagem para *aplicação de patch sob demanda*. Esse parâmetro garante que a primeira instrução de cada função tenha dois bytes, o que é necessário para aplicação de patch sob demanda.  
  
     Para obter mais informações, consulte [/hotpatch (criar imagem capaz de aplicar patches sob demanda)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
-   **DebugInformationFormat**  
  
     Parâmetro String opcional.  
  
     Selecione o tipo de informações de depuração criadas para seu programa e se essas informações são mantidas em arquivos de objeto (.obj) ou em um banco de dados de programa (PDB).  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **OldStyle** - **/Z7**  
  
    -   **ProgramDatabase** - **/Zi**  
  
    -   **EditAndContinue** - **/ZI**  
  
     Para obter mais informações, consulte [/Z7, /Zd, /Zi, /ZI (formato de informação de depuração)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).  
  
-   **DisableLanguageExtensions**  
  
     Parâmetro Boolean opcional.  
  
     Se **true**, dirá ao compilador para emitir um erro para construções de linguagem que não sejam compatíveis com ANSI C ou ANSI C++.  
  
     Para obter mais informações, consulte a opção **/Za** em [/Za, /Ze (Desabilitar Extensões de Idioma)](/visual-cpp/build/reference/za-ze-disable-language-extensions).  
  
-   **DisableSpecificWarnings**  
  
     Parâmetro String[] opcional.  
  
     Desabilita os números de aviso especificados em uma lista delimitada por ponto e vírgula.  
  
     Para obter mais informações, consulte a opção `/wd` em [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nível de Aviso)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **EnableEnhancedInstructionSet**  
  
     Parâmetro String opcional.  
  
     Especifica a arquitetura para a geração de código que usa as instruções SSE (Streaming SIMD Extensions) e SSE2 (Streaming SIMD Extensions 2).  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **StreamingSIMDExtensions** - **/arch:SSE**  
  
    -   **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
     Para obter mais informações, consulte [/arch (x86)](/visual-cpp/build/reference/arch-x86).  
  
-   **EnableFiberSafeOptimizations**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, dê suporte a segurança de fibra para dados alocados usando armazenamento local de thread estático, ou seja, dados alocados usando `__declspec(thread)`.  
  
     Para obter mais informações, consulte [/GT (suporte para armazenamento em fibra-thread safe-local)](/visual-cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
-   **EnablePREfast**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, habilitará análise de código.  
  
     Para obter mais informações, consulte [/analyze (Análise de Código)](/visual-cpp/build/reference/analyze-code-analysis).  
  
-   **ErrorReporting**  
  
     Parâmetro String opcional.  
  
     Permite que você forneça informações de ICE (erro interno do compilador) diretamente à Microsoft. Por padrão, a configuração em compilações do IDE é **Aviso** e a configuração em compilações de linha de comando é **Fila**.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **None** - **/errorReport:none**  
  
    -   **Prompt** - **/errorReport:prompt**  
  
    -   **Queue** - **/errorReport:queue**  
  
    -   **Send** - **/errorReport:send**  
  
     Para obter mais informações, consulte [/errorReport (relatório de erros internos do compilador)](/visual-cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
-   **ExceptionHandling**  
  
     Parâmetro String opcional.  
  
     Especifica o modelo de tratamento de exceções a ser utilizado pelo compilador.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **false** - *\<none>*  
  
    -   **Async** - **/EHa**  
  
    -   **Sync** - **/EHsc**  
  
    -   **SyncCThrow** - **/EHs**  
  
     Para obter mais informações, consulte [/EH (modelo de tratamento de exceção)](/visual-cpp/build/reference/eh-exception-handling-model).  
  
-   **ExpandAttributedSource**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, criará um arquivo de listagem com atributos expandidos injetados no arquivo de origem.  
  
     Para obter mais informações, consulte [/Fx (mesclar código injetado)](/visual-cpp/build/reference/fx-merge-injected-code).  
  
-   **FavorSizeOrSpeed**  
  
     Parâmetro String opcional.  
  
     Especifica se tamanho ou velocidade do código deve ser favorecido.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Neither** - *\<none>*  
  
    -   **Size** - **/Os**  
  
    -   **Speed** - **/Ot**  
  
     Para obter mais informações, consulte [/Os, /Ot (favorecer código pequeno, favorecer código rápido)](/visual-cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
-   **FloatingPointExceptions**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, habilitará o modelo de exceção de ponto flutuante confiável. As exceções serão geradas imediatamente depois de serem disparadas.  
  
     Para obter mais informações, consulte a opção o /**fp:except** em [/fp (Especificar Comportamento de Ponto Flutuante)](/visual-cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **FloatingPointModel**  
  
     Parâmetro String opcional.  
  
     Define o modelo de ponto flutuante.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Precise** - **/fp:precise**  
  
    -   **Strict** - **/fp:strict**  
  
    -   **Fast** - **/fp:fast**  
  
     Para obter mais informações, consulte [/fp (especificar comportamento de ponto flutuante)](/visual-cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **ForceConformanceInForLoopScope**  
  
     Parâmetro Boolean opcional.  
  
     Se `true`, implementará o comportamento padrão do C++ em loops [for](/visual-cpp/cpp/for-statement-cpp) que usem extensões da Microsoft ([/Ze](/visual-cpp/build/reference/za-ze-disable-language-extensions)).  
  
     Para obter mais informações, consulte [/Zc:forScope (forçar conformidade para escopo de loop)](http://msdn.microsoft.com/Library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
-   **ForcedIncludeFiles**  
  
     Parâmetro `String[]` opcional.  
  
     Faz o pré-processador processar um ou mais arquivos de cabeçalho especificados.  
  
     Para obter mais informações, consulte [/FI (nomear arquivo de include forçado)](/visual-cpp/build/reference/fi-name-forced-include-file).  
  
-   **ForcedUsingFiles**  
  
     Parâmetro **String[]** opcional.  
  
     Faz o pré-processador processar um ou mais arquivos **#using** especificados.  
  
     Para obter mais informações, consulte [/FU (nome forçado #usando arquivo)](/visual-cpp/build/reference/fu-name-forced-hash-using-file).  
  
-   **FunctionLevelLinking**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, permitirá que o compilador empacote funções individuais na forma de funções empacotadas (COMDATs).  
  
     Para obter mais informações, consulte [/Gy (habilitar vinculação em nível de função)](/visual-cpp/build/reference/gy-enable-function-level-linking).  
  
-   **GenerateXMLDocumentationFiles**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, fará o compilador processar comentários da documentação em arquivos de código-fonte e criará um arquivo .xdc para cada arquivo de código-fonte que tenha comentários de documentação.  
  
     Para obter mais informações, consulte [/doc (processar comentários da documentação) (C/C++)](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp). Consulte também o parâmetro **XMLDocumentationFileName** nesta tabela.  
  
-   **IgnoreStandardIncludePath**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, evitará que o compilador pesquise os arquivos de inclusão em diretórios especificados nas variáveis de ambiente PATH e INCLUDE.  
  
     Para obter mais informações, consulte [/X (ignorar caminhos de inclusão padrão)](/visual-cpp/build/reference/x-ignore-standard-include-paths).  
  
-   **InlineFunctionExpansion**  
  
     Parâmetro **String** opcional.  
  
     Especifica o nível de expansão de função embutida para o build.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Default** - *\<none>*  
  
    -   **Disabled** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **/Ob1**  
  
    -   **AnySuitable** - **/Ob2**  
  
     Para obter mais informações, consulte [/Ob (expansão de função embutida)](/visual-cpp/build/reference/ob-inline-function-expansion).  
  
-   **IntrinsicFunctions**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, substituirá algumas chamadas de função com formas da função intrínsecas ou especiais de outra maneira que ajudem o aplicativo a ser executado mais rapidamente.  
  
     Para obter mais informações, consulte [/Oi (gerar funções intrínsecas)](/visual-cpp/build/reference/oi-generate-intrinsic-functions).  
  
-   **MinimalRebuild**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, habilitará recompilação mínima, que determina se os arquivos de origem C++ que incluem definições de classe C++ alteradas (armazenadas nos arquivos de cabeçalho (.h)) devem ser recompilados.  
  
     Para obter mais informações, consulte [/Gm (habilitar recompilação mínima)](/visual-cpp/build/reference/gm-enable-minimal-rebuild).  
  
-   **MultiProcessorCompilation**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, use vários processadores para compilar. Esse parâmetro cria um processo para cada processador efetivo no seu computador.  
  
     Para obter mais informações, consulte [/MP (compilar com vários processos)](/visual-cpp/build/reference/mp-build-with-multiple-processes). Consulte também o parâmetro **ProcessorNumber** nesta tabela.  
  
-   **ObjectFileName**  
  
     Parâmetro **String** opcional.  
  
     Especifica um nome de arquivo de objeto (.obj) ou diretório a ser usado no lugar do padrão.  
  
     Para obter mais informações, consulte [/Fo (nome do arquivo-objeto)](/visual-cpp/build/reference/fo-object-file-name).  
  
-   **ObjectFiles**  
  
     Parâmetro **String[]** opcional.  
  
     Uma lista de arquivos de objeto.  
  
-   **OmitDefaultLibName**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, omitirá o nome da biblioteca em tempo de execução C padrão do arquivo de objeto (.obj). Por padrão, o compilador coloca o nome da biblioteca no arquivo .obj para direcionar o vinculador à biblioteca correta.  
  
     Para obter mais informações, consulte [/Zl (omitir o nome da biblioteca padrão)](/visual-cpp/build/reference/zl-omit-default-library-name).  
  
-   **OmitFramePointers**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, suprimirá a criação de ponteiros de quadro na pilha de chamadas.  
  
     Para obter mais informações, consulte [/Oy (omissão do ponteiro de quadro)](/visual-cpp/build/reference/oy-frame-pointer-omission).  
  
-   **OpenMPSupport**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, fará o compilador processar cláusulas e diretivas OpenMP.  
  
     Para obter mais informações, consulte [/openmp (habilitar suporte a OpenMP 2.0)](/visual-cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
-   **Optimization**  
  
     Parâmetro **String** opcional.  
  
     Especifica várias otimizações de código para velocidade e tamanho.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Disabled** - **/Od**  
  
    -   **MinSpace** - **/O1**  
  
    -   **MaxSpeed** - **/O2**  
  
    -   **Full** - **/Ox**  
  
     Para obter mais informações, consulte Opções de [/S (otimizar código)](/visual-cpp/build/reference/o-options-optimize-code).  
  
-   **PrecompiledHeader**  
  
     Parâmetro **String** opcional.  
  
     Crie ou use um arquivo de cabeçalho pré-compilado (.pch) durante o build.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **NotUsing** - *\<none>*  
  
    -   **Create** - **/Yc**  
  
    -   **Use** - **/Yu**  
  
     Para obter mais informações, consulte [/Yc (Criar arquivo de cabeçalho pré-compilado)](/visual-cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (Usar arquivo de cabeçalho pré-compilado)](/visual-cpp/build/reference/yu-use-precompiled-header-file). Consulte também os parâmetros **PrecompiledHeaderFile** e **PrecompiledHeaderOutputFile** nessa tabela.  
  
-   **PrecompiledHeaderFile**  
  
     Parâmetro **String** opcional.  
  
     Especifica um nome de arquivo de cabeçalho pré-compilado para criar ou usar.  
  
     Para obter mais informações, consulte [/Yc (Criar arquivo de cabeçalho pré-compilado)](/visual-cpp/build/reference/yc-create-precompiled-header-file) e [/Yu (Usar arquivo de cabeçalho pré-compilado)](/visual-cpp/build/reference/yu-use-precompiled-header-file).  
  
-   **PrecompiledHeaderOutputFile**  
  
     Parâmetro **String** opcional.  
  
     Especifica um nome de caminho para um cabeçalho pré-compilado em vez de usar o nome do caminho padrão.  
  
     Para obter mais informações, consulte [/Fp (arquivo .Pch de nome)](/visual-cpp/build/reference/fp-name-dot-pch-file).  
  
-   **PreprocessKeepComments**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, preservará comentários durante o pré-processamento.  
  
     Para obter mais informações, consulte [/C (Preservar Comentários Durante o Pré-Processamento)](/visual-cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
-   **PreprocessorDefinitions**  
  
     Parâmetro `String[]` opcional.  
  
     Define um símbolo de pré-processamento para seu arquivo de origem.  
  
     Para obter mais informações, consulte [/D (definições de pré-processador)](/visual-cpp/build/reference/d-preprocessor-definitions).  
  
-   **PreprocessOutput**  
  
     Parâmetro `ITaskItem[]` opcional.  
  
     Define uma matriz de itens de saída do pré-processador que podem ser consumidos e emitidos por tarefas.  
  
-   **PreprocessOutputPath**  
  
     Parâmetro `String` opcional.  
  
     Especifica o nome do arquivo de saída para o qual o parâmetro **PreprocessToFile** grava a saída pré-processada.  
  
     Para obter mais informações, consulte [/Fi (pré-processar nome de arquivo de saída)](/visual-cpp/build/reference/fi-preprocess-output-file-name).  
  
-   **PreprocessSuppressLineNumbers**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, pré-processará arquivos de origem em C e C++ e copiará os arquivos pré-processados para o dispositivo de saída padrão.  
  
     Para obter mais informações, consulte [/EP (pré-processar para stdout Sem Diretivas #line)](/visual-cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
-   **PreprocessToFile**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, pré-processará arquivos de origem em C e C++ e gravará a saída pré-processada em um arquivo.  
  
     Para obter mais informações, consulte [/P (pré-processar para um arquivo)](/visual-cpp/build/reference/p-preprocess-to-a-file).  
  
-   **ProcessorNumber**  
  
     Parâmetro `Integer` opcional.  
  
     Especifica o número máximo de processadores a serem usados em uma compilação multiprocessador. Use esse parâmetro em combinação com o parâmetro **MultiProcessorCompilation**.  
  
-   **ProgramDataBaseFileName**  
  
     Parâmetro `String` opcional.  
  
     Especifica um nome de arquivo para o arquivo PDB (banco de dados do programa).  
  
     Para obter mais informações, consulte [/Fd (nome de arquivo de banco de dados do programa)](/visual-cpp/build/reference/fd-program-database-file-name).  
  
-   **RuntimeLibrary**  
  
     Parâmetro `String` opcional.  
  
     Indica se um módulo com multithread é uma DLL e seleciona versões de varejo ou de depuração da biblioteca em tempo de execução.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **MultiThreaded** - **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/MD**  
  
    -   **MultiThreadedDebugDLL** - **/MDd**  
  
     Para obter mais informações, consulte [/MD, /MT, /LD (usar biblioteca em tempo de execução)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library).  
  
-   **RuntimeTypeInfo**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, adicionará código para verificar os tipos de objeto C++ no tempo de execução (informações de tipo de tempo de execução).  
  
     Para obter mais informações, consulte [/GR (habilitar informações de tipo de tempo de execução)](/visual-cpp/build/reference/gr-enable-run-time-type-information).  
  
-   **ShowIncludes**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, fará o compilador gerar uma lista dos arquivos de inclusão.  
  
     Para obter mais informações, consulte [/showIncludes (listar arquivos de inclusão)](/visual-cpp/build/reference/showincludes-list-include-files).  
  
-   **SmallerTypeCheck**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, relatará um erro em tempo de execução se um valor for atribuído a um tipo de dados menor e provocará perda de dados.  
  
     Para obter mais informações, consulte a opção **/RTCc** em [/RTC (Verificações de Erro em Tempo de Execução)](/visual-cpp/build/reference/rtc-run-time-error-checks).  
  
-   **Sources**  
  
     Parâmetro `ITaskItem[]` obrigatório.  
  
     Especifica uma lista de arquivos de origem separados por espaços.  
  
-   **StringPooling**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, permitirá que o compilador crie uma cópia de cadeias de caracteres idênticas na imagem do programa.  
  
     Para obter mais informações, consulte [/GF (eliminar cadeias de caracteres duplicadas)](/visual-cpp/build/reference/gf-eliminate-duplicate-strings).  
  
-   **StructMemberAlignment**  
  
     Parâmetro `String` opcional.  
  
     Especifica o alinhamento de byte para todos os membros em uma estrutura.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **Default** - **/Zp1**  
  
    -   **1Byte** - **/Zp1**  
  
    -   **2Bytes** - **/Zp2**  
  
    -   **4Bytes** - **/Zp4**  
  
    -   **8Bytes** - **/Zp8**  
  
    -   **16Bytes** - **/Zp16**  
  
     Para obter mais informações, consulte [/Zp (Alinhamento de Membro de Struct)](/visual-cpp/build/reference/zp-struct-member-alignment).  
  
-   **SuppressStartupBanner**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.  
  
     Para obter mais informações, consulte [/nologo (suprimir faixa de inicialização) (C/C++)](/visual-cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
-   **TrackerLogDirectory**  
  
     Parâmetro `String` opcional.  
  
     Especifica o diretório intermediário em que os logs de rastreamento para essa tarefa são armazenados.  
  
     Para obter mais informações, consulte os parâmetros **TLogReadFiles** e **TLogWriteFiles** nesta tabela.  
  
-   **TreatSpecificWarningsAsErrors**  
  
     Parâmetro **String[]** opcional.  
  
     Trata a lista especificada de avisos do compilador como erros.  
  
     Para obter mais informações, consulte a opção **/we**`n` em [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nível de Aviso)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWarningAsError**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, tratará todos os avisos do compilador como erros.  
  
     Para obter mais informações, consulte a opção **/WX** em [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nível de aviso)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWChar_tAsBuiltInType**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, trate o tipo `wchar_t` como um tipo nativo.  
  
     Para obter mais informações, consulte [/Zc:wchar_t (wchar_t é o tipo nativo)](http://msdn.microsoft.com/Library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, cancelará a definição de símbolos específicos da Microsoft que o compilador definir.  
  
     Para obter mais informações, consulte a opção **/u** em [/U, /u (Excluir Símbolos)](/visual-cpp/build/reference/u-u-undefine-symbols).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parâmetro `String[]` opcional.  
  
     Especifica uma lista de um ou mais símbolos de pré-processador a excluir.  
  
     Para obter mais informações, consulte a opção **/U** em [/U, /u (excluir símbolos)](/visual-cpp/build/reference/u-u-undefine-symbols).  
  
-   **UseFullPaths**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, exibirá o caminho completo dos arquivos de código-fonte passados para o compilador no diagnóstico.  
  
     Para obter mais informações, consulte [/FC (caminho completo do arquivo de código-fonte no diagnóstico)](/visual-cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
-   **UseUnicodeForAssemblerListing**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, fará o arquivo de saída ser criado em formato UTF-8.  
  
     Para obter mais informações, consulte a opção **/FAu** em [/FA, /Fa (Arquivo de Listagem)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **WarningLevel**  
  
     Parâmetro `String` opcional.  
  
     Especifica o nível mais alto de aviso que deverá ser gerado pelo compilador.  
  
     Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.  
  
    -   **TurnOffAllWarnings** - **/W0**  
  
    -   **Level1** - **/W1**  
  
    -   **Level2** - **/W2**  
  
    -   **Level3** - **/W3**  
  
    -   **Level4** - **/W4**  
  
    -   **EnableAllWarnings** - **/Wall**  
  
     Para obter mais informações, consulte a opção **/W***n* em [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nível de Aviso)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **WholeProgramOptimization**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, habilitará a otimização de todo o programa.  
  
     Para obter mais informações, consulte [/GL (otimização de programa inteiro)](/visual-cpp/build/reference/gl-whole-program-optimization).  
  
-   **XMLDocumentationFileName**  
  
     Parâmetro `String` opcional.  
  
     Especifica o nome dos arquivos de documentação XML gerados. Esse parâmetro pode ser um nome de arquivo ou de diretório.  
  
     Para obter mais informações, consulte o argumento `name` em [/doc ( Comentários da Documentação do Processo) (C/C++)](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp). Consulte também o parâmetro **GenerateXMLDocumentationFiles** nesta tabela.  
  
-   **MinimalRebuildFromTracking**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, um build incremental controlada será executada; se `false`, será executada uma recompilação.  
  
-   **TLogReadFiles**  
  
     Parâmetro `ITaskItem[]` opcional.  
  
     Especifica uma matriz de itens que representam os *logs de acompanhamento do arquivo de leitura*.  
  
     Um log de acompanhamento do arquivo de leitura (.tlog) contém os nomes dos arquivos de entrada lidos por uma tarefa e é usado pelo sistema de build do projeto para dar suporte a compilações incrementais. Para obter mais informações, consulte os parâmetros **TrackerLogDirectory** e **TrackFileAccess** nesta tabela.  
  
-   **TLogWriteFiles**  
  
     Parâmetro `ITaskItem[]` opcional.  
  
     Especifica uma matriz de itens que representam os *logs de acompanhamento do arquivo de gravação*.  
  
     Um log de acompanhamento de arquivo de gravação (.tlog) contém os nomes dos arquivos de saída gravados por uma tarefa e é usado pelo sistema de build do projeto para dar suporte a compilações incrementais. Para obter mais informações, consulte os parâmetros **TrackerLogDirectory** e **TrackFileAccess** nesta tabela.  
  
-   **TrackFileAccess**  
  
     Parâmetro `Boolean` opcional.  
  
     Se `true`, controlará os padrões de acesso de arquivo.  
  
     Para obter mais informações, consulte os parâmetros **TLogReadFiles** e **TLogWriteFiles** nesta tabela.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)


<!--HONumber=Feb17_HO4-->


