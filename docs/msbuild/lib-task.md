---
title: "Tarefa LIB | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.Name"
  - "VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors"
  - "VC.Project.VCLibrarianTool.Verbose"
  - "vc.task.lib"
  - "VC.Project.VCLibrarianTool.ErrorReporting"
  - "VC.Project.VCLibrarianTool.LinkLibraryDependencies"
  - "VC.Project.VCLibrarianTool.LinkTimeCodeGeneration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "tarefa LIB (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), tarefa LIB"
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa LIB
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsula a ferramenta Gerenciador de biblioteca da Microsoft de 32 bits, lib.exe.  O Gerenciador de biblioteca cria e gerencia uma biblioteca de arquivos de objeto de arquivo formato COFF \(Common Object\).  O Gerenciador de biblioteca também pode criar arquivos de exportação e importar bibliotecas para definições de referência exportada.  Para obter mais informações, consulte [Referência LIB](/visual-cpp/build/reference/lib-reference) e [Executando LIB](/visual-cpp/build/reference/running-lib).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **LIB**.  A maioria dos parâmetros da tarefa correspondem a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**AdditionalDependencies**|Parâmetro **String\[\]** opcional.<br /><br /> Especifica itens adicionais a serem adicionados à linha de comando.|  
|**AdditionalLibraryDirectories**|Parâmetro **String\[\]** opcional.<br /><br /> Substitui o caminho da biblioteca de ambiente.  Especifique um nome de diretório.<br /><br /> Para obter mais informações, consulte [\/LIBPATH \(Libpath adicional\)](/visual-cpp/build/reference/libpath-additional-libpath).|  
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções lib.exe conforme especificado na linha de comando.  Por exemplo, **"***\/option1 \/option2 \/option\#*".  Use esse parâmetro para especificar opções de lib.exe que não são representadas por qualquer outra **LIB** de tarefa.<br /><br /> Para obter mais informações, consulte [Executando LIB](/visual-cpp/build/reference/running-lib).|  
|**DisplayLibrary**|Parâmetro **String** opcional.<br /><br /> Exibe informações sobre a biblioteca de saída.  Especifique um nome de arquivo para redirecionar as informações para um arquivo.  Especifique "CON" ou nada para redirecionar as informações para o console.<br /><br /> Esse parâmetro corresponde do **\/LIST** opção de lib.exe.|  
|**ErrorReporting**|Parâmetro **String** opcional.<br /><br /> Especifica como enviar à Microsoft informações de erro interno se lib.exe falhar em tempo de execução.<br /><br /> Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.<br /><br /> -   **NoErrorReport** \- **\/ERRORREPORT:NONE**<br />-   **PromptImmediately** \- **\/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** \- **\/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** \- **\/ERRORREPORT:SEND**<br /><br /> Para obter mais informações, consulte o **\/ERRORREPORT** a opção de linha de comando na [Executando LIB](/visual-cpp/build/reference/running-lib).|  
|**ExportNamedFunctions**|Parâmetro **String\[\]** opcional.<br /><br /> Especifica uma ou mais funções para exportar.<br /><br /> Esse parâmetro corresponde do **\/EXPORT:** opção de lib.exe.|  
|**ForceSymbolReferences**|Parâmetro **String** opcional.<br /><br /> Força lib.exe para incluir uma referência ao símbolo especificado.<br /><br /> Esse parâmetro corresponde do **\/INCLUDE:** opção de lib.exe.|  
|**IgnoreAllDefaultLibraries**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, remove todas as bibliotecas padrão na lista de bibliotecas que lib.exe pesquisa quando ele resolver referências externas.<br /><br /> Esse parâmetro corresponde ao formato sem parâmetros de **\/NODEFAULTLIB** opção de lib.exe.|  
|**IgnoreSpecificDefaultLibraries**|Parâmetro **String\[\]** opcional.<br /><br /> Remove as bibliotecas especificadas na lista de bibliotecas que lib.exe pesquisa quando ele resolver referências externas.<br /><br /> Esse parâmetro corresponde do **\/NODEFAULTLIB** opção de lib.exe que usa um `library` argumento.|  
|**LinkLibraryDependencies**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, especifica que as saídas de biblioteca das dependências do projeto são automaticamente vinculadas.|  
|**LinkTimeCodeGeneration**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, especifica a geração de código link\-time.<br /><br /> Esse parâmetro corresponde do **\/LCTG** opção de lib.exe.|  
|**MinimumRequiredVersion**|Parâmetro **String** opcional.<br /><br /> Especifica a versão mínima necessária do subsistema.  Especifique uma lista delimitada por vírgulas de números decimais no intervalo de 0 a 65535.|  
|**ModuleDefinitionFile**|Parâmetro **String** opcional.<br /><br /> Especifica o nome do arquivo de definição de módulo \(. def\).<br /><br /> Esse parâmetro corresponde do **\/DEF** opção de lib.exe que usa um `filename` argumento.|  
|**Name**|Parâmetro **String** opcional.<br /><br /> Quando uma biblioteca de importação é criada, especifica o nome da DLL para o qual a biblioteca de importação está sendo criada.<br /><br /> Esse parâmetro corresponde do **\/NAME** opção de lib.exe que usa um `filename` argumento.|  
|**OutputFile**|Parâmetro **String** opcional.<br /><br /> Substitui o padrão do nome e o local do programa que lib.exe cria.<br /><br /> Esse parâmetro corresponde do **\/OUT** opção de lib.exe que usa um `filename` argumento.|  
|**RemoveObjects**|Parâmetro **String\[\]** opcional.<br /><br /> Omite o objeto especificado da biblioteca de saída.  Lib.exe cria uma biblioteca de saída, combinando todos os objetos \(seja em arquivos de objeto ou bibliotecas\) e excluindo todos os objetos que são especificados por essa opção.<br /><br /> Esse parâmetro corresponde do **\/REMOVE** opção de lib.exe que usa um `membername` argumento.|  
|**Sources**|Parâmetro `ITaskItem[]` obrigatório.<br /><br /> Especifica uma lista dos arquivos de origem separados por espaços.|  
|**SubSystem**|Parâmetro **String** opcional.<br /><br /> Especifica o ambiente para o executável.  A escolha do subsistema afeta o símbolo de ponto de entrada ou a função de ponto de entrada.<br /><br /> Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.<br /><br /> -   **Console** \- **\/SUBSYSTEM:CONSOLE**<br />-   **Windows** \- **\/SUBSYSTEM:WINDOWS**<br />-   **Native** \- **\/SUBSYSTEM:NATIVE**<br />-   **EFI Application** \- **\/SUBSYSTEM:EFI\_APPLICATION**<br />-   **EFI Boot Service Driver** \- **\/SUBSYSTEM:EFI\_BOOT\_SERVICE\_DRIVER**<br />-   **EFI ROM** \- **\/SUBSYSTEM:EFI\_ROM**<br />-   **EFI Runtime** \- **\/SUBSYSTEM:EFI\_RUNTIME\_DRIVER**<br />-   **WindowsCE** \-**\/SUBSYSTEM:WINDOWSCE**ReplaceThisText<br />-   **POSIX** \- **\/SUBSYSTEM:POSIX**<br /><br /> Para obter mais informações, consulte [\/SUBSYSTEM \(especificar subsistema\)](/visual-cpp/build/reference/subsystem-specify-subsystem).|  
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impede a exibição da mensagem de número de versão e copyright quando a tarefa é iniciada.<br /><br /> Para obter mais informações, consulte o **\/NOLOGO** opção em [Executando LIB](/visual-cpp/build/reference/running-lib).|  
|**TargetMachine**|Parâmetro **String** opcional.<br /><br /> Especifica a plataforma de destino para o programa ou DLL.<br /><br /> Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.<br /><br /> -   **MachineARM** \- **\/MACHINE:ARM**<br />-   **MachineEBC** \- **\/MACHINE:EBC**<br />-   **MachineIA64** \- **\/MACHINE:IA64**<br />-   **MachineMIPS** \- **\/MACHINE:MIPS**<br />-   **MachineMIPS16** \- **\/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** \-**\/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** \- **\/MACHINE:MIPSFPU16**<br />-   **MachineSH4** \- **\/MACHINE:SH4**<br />-   **MachineTHUMB** \- **\/MACHINE:THUMB**<br />-   **MachineX64** \- **\/MACHINE:X64**<br />-   **MachineX86** \- **\/MACHINE:X86**<br /><br /> Para obter mais informações, consulte [\/MACHINE \(especificar plataforma de destino\)](/visual-cpp/build/reference/machine-specify-target-platform).|  
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório de log do controlador.|  
|**TreatLibWarningAsErrors**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, faz com que o **LIB** tarefa não gere um arquivo de saída se lib.exe gera um aviso.  Se `false`, um arquivo de saída é gerado.<br /><br /> Para obter mais informações, consulte o **\/WX** opção em [Executando LIB](/visual-cpp/build/reference/running-lib).|  
|**UseUnicodeResponseFiles**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, instrui o sistema do projeto a gerar arquivos de resposta UNICODE quando o bibliotecário é gerado.  Especifique `true` quando os arquivos no projeto tiverem caminhos UNICODE.|  
|**Verbose**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, exibe detalhes sobre o progresso da sessão; isso inclui os nomes dos arquivos. obj que está sendo adicionados.  As informações enviadas para a saída padrão e podem ser redirecionadas para um arquivo.<br /><br /> Para obter mais informações, consulte o **\/VERBOSE** opção [Executando LIB](/visual-cpp/build/reference/running-lib).|  
  
## Comentários  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)