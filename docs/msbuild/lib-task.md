---
title: Tarefa LIB | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
caps.latest.revision: 7
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 0796bf0d449822472cfc3a5317620491ed276d78
ms.lasthandoff: 04/05/2017

---
# <a name="lib-task"></a>Tarefa LIB
Encapsula a ferramenta Gerenciador de Biblioteca de 32 bits da Microsoft, lib.exe. O Gerenciador de Biblioteca cria e gerencia uma biblioteca de arquivos-objetos de formato COFF. O Gerenciador de Biblioteca também pode criar arquivos de exportação e importar bibliotecas para referenciar definições exportadas. Para obter mais informações, consulte [Referência de LIB](/cpp/build/reference/lib-reference) e [Executando LIB](/cpp/build/reference/running-lib).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **LIB**. A maioria dos parâmetros de tarefa corresponde a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**AdditionalDependencies**|Parâmetro **String[]** opcional.<br /><br /> Especifica itens adicionais para adicionar à linha de comando.|  
|**AdditionalLibraryDirectories**|Parâmetro **String[]** opcional.<br /><br /> Substitui o caminho da biblioteca de ambiente. Especifique um nome de diretório.<br /><br /> Para obter mais informações, consulte [/LIBPATH (Libpath Adicional)](/cpp/build/reference/libpath-additional-libpath).|  
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções lib.exe, conforme especificado na linha de comando. Por exemplo, **"***/option1 /option2 /option#*". Use esse parâmetro para especificar opções lib.exe que não são representadas por qualquer outro parâmetro de tarefa **LIB**.<br /><br /> Para obter mais informações, consulte [Executando LIB](/cpp/build/reference/running-lib).|  
|**DisplayLibrary**|Parâmetro **String** opcional.<br /><br /> Exibe informações sobre a biblioteca de saída. Especifique um nome de arquivo para redirecionar as informações para um arquivo. Especifique "CON" ou não para redirecionar as informações para o console.<br /><br /> Esse parâmetro corresponde à opção **/LIST** de lib.exe.|  
|**ErrorReporting**|Parâmetro **String** opcional.<br /><br /> Especifica como enviar informações de erro interno à Microsoft se o lib.exe falhar em tempo de execução.<br /><br /> Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Para obter mais informações, consulte a opção de linha de comando **/ERRORREPORT** em [Executando LIB](/cpp/build/reference/running-lib).|  
|**ExportNamedFunctions**|Parâmetro **String[]** opcional.<br /><br /> Especifica uma ou mais funções a serem exportadas.<br /><br /> Esse parâmetro corresponde à opção **/EXPORT** de lib.exe.|  
|**ForceSymbolReferences**|Parâmetro **String** opcional.<br /><br /> Força o lib.exe a incluir uma referência ao símbolo especificado.<br /><br /> Esse parâmetro corresponde à opção **/INCLUDE:** de lib.exe.|  
|**IgnoreAllDefaultLibraries**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, removerá todas as bibliotecas padrão da lista de bibliotecas pesquisadas pelo lib.exe ao resolver referências externas.<br /><br /> Esse parâmetro corresponde ao formato sem parâmetros da opção **/NODEFAULTLIB** do lib.exe.|  
|**IgnoreSpecificDefaultLibraries**|Parâmetro **String[]** opcional.<br /><br /> Remove as bibliotecas especificadas da lista de bibliotecas pesquisadas pelo lib.exe ao resolver referências externas.<br /><br /> Esse parâmetro corresponde à opção **/NODEFAULTLIB** do lib.exe, que usa um argumento `library`.|  
|**LinkLibraryDependencies**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, especificará que as saídas de biblioteca das dependências do projeto serão vinculadas automaticamente.|  
|**LinkTimeCodeGeneration**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, especificará a geração do código de tempo de vinculação.<br /><br /> Esse parâmetro corresponde à opção **/LCTG** de lib.exe.|  
|**MinimumRequiredVersion**|Parâmetro **String** opcional.<br /><br /> Especifica a versão mínima necessária do subsistema. Especifique uma lista delimitada por vírgulas de números decimais no intervalo de 0 a 65535.|  
|**ModuleDefinitionFile**|Parâmetro **String** opcional.<br /><br /> Especifica o nome do arquivo de definição de módulo (.def).<br /><br /> Esse parâmetro corresponde à opção **/DEF** do lib.exe, que usa um argumento `filename`.|  
|**Nome**|Parâmetro **String** opcional.<br /><br /> Ao compilar uma biblioteca de importação, especifica o nome da DLL para a qual a biblioteca de importação está sendo compilada.<br /><br /> Esse parâmetro corresponde à opção **/NAME** do lib.exe, que usa um argumento `filename`.|  
|**OutputFile**|Parâmetro **String** opcional.<br /><br /> Substitui o nome padrão e o local do programa criado pelo lib.exe.<br /><br /> Esse parâmetro corresponde à opção **/OUT** do lib.exe, que usa um argumento `filename`.|  
|**RemoveObjects**|Parâmetro **String[]** opcional.<br /><br /> Omite o objeto especificado da biblioteca de saída. O lib.exe cria uma biblioteca de saída ao combinar todos os objetos (seja em arquivos-objetos ou bibliotecas) e, em seguida, excluir objetos especificados por essa opção.<br /><br /> Esse parâmetro corresponde à opção **/REMOVE** do lib.exe, que usa um argumento `membername`.|  
|**Sources**|Parâmetro `ITaskItem[]` obrigatório.<br /><br /> Especifica uma lista de arquivos de origem separados por espaços.|  
|**SubSystem**|Parâmetro **String** opcional.<br /><br /> Especifica o ambiente para o executável. A escolha do subsistema afeta o símbolo do ponto de entrada ou a função de ponto de entrada.<br /><br /> Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.<br /><br /> -   **Console** - **/SUBSYSTEM:CONSOLE**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Nativo** - **/SUBSYSTEM:NATIVE**<br />-   **Aplicativo EFI** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **Driver de Serviço de Inicialização EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **Tempo de Execução de EFI** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**ReplaceThisText<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Para obter mais informações, consulte [/SUBSYSTEM (Especificar Subsistema)](/cpp/build/reference/subsystem-specify-subsystem).|  
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, consulte a opção **/NOLOGO** em [Executando LIB](/cpp/build/reference/running-lib).|  
|**TargetMachine**|Parâmetro **String** opcional.<br /><br /> Especifica a plataforma de destino para o programa ou DLL.<br /><br /> Especifique um dos valores a seguir, cada um correspondendo a uma opção de linha de comando.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Para obter mais informações, consulte [/MACHINE (Especificar Plataforma de Destino)](/cpp/build/reference/machine-specify-target-platform).|  
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório de log de rastreamento.|  
|**TreatLibWarningAsErrors**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, fará com que a tarefa **LIB** não gere um arquivo de saída se lib.exe gerar um aviso. Se `false`, um arquivo de saída será gerado.<br /><br /> Para obter mais informações, consulte a opção **/WX** em [Executando LIB](/cpp/build/reference/running-lib).|  
|**UseUnicodeResponseFiles**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, instruirá o sistema do projeto a gerar arquivos de resposta UNICODE quando o bibliotecário for gerado. Especifique `true` quando os arquivos no projeto tiverem caminhos UNICODE.|  
|**Verbose**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, exibirá detalhes sobre o progresso da sessão; isso inclui os nomes dos arquivos .obj que estão sendo adicionados. A informação é enviada para uma saída padrão e pode ser redirecionada para um arquivo.<br /><br /> Para obter mais informações, consulte a opção **/VERBOSE** em [Executando LIB](/cpp/build/reference/running-lib).|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
