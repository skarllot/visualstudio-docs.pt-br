---
title: "Deputar um ou mais processos no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.programs"
  - "vs.debug.processes.attaching"
  - "vs.debug.activeprogram"
  - "vs.debug.attaching"
  - "vs.debug.attachedprocesses"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Deputar um ou mais processos no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Veja como iniciar processos de depuração, alternar entre processos, interromper e continuar a execução, percorrer o código\-fonte, interromper a depuração e terminar ou desanexar dos processos.  
  
##  <a name="BKMK_Contents"></a> Conteúdo  
 [Configurar o comportamento de execução de vários processos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Localize a fonte e os arquivos de símbolo (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Iniciar vários processos em uma solução VS, anexar a um processo, iniciar automaticamente um processo no depurador](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Alternar entre processos, interromper e continuar a execução, percorrer origem](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Parar a depuração, finalizar ou desanexar dos processos](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Configurar o comportamento de execução de vários processos  
 Por padrão, quando vários processos são executados no depurador, os comandos de quebra, avanço e interrupção do depurador geralmente afetam todos os processos.  Por exemplo, quando um processo é suspenso em um ponto de interrupção, a execução de todos outros processos é suspendida também.  Você pode alterar esse comportamento padrão para obter mais controle sobre os destinos dos comandos de execução.  
  
1.  No menu de **Depurar**, escolha **Opções e Configurações**.  
  
2.  Na página **Depuração**, **Geral**, desmarque a caixa de seleção **Interromper todos os processos quando um processo for interrompido**.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Localize a fonte e os arquivos de símbolo \(.pdb\)  
 Para navegar no código\-fonte de um processo, o depurador precisa acessar os arquivos de origem e os arquivos do símbolo do processo.  Consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Se você não conseguir acessar arquivos para um processo, poderá navegar usando a janela de desmontagem.  Consulte [Como usar a janela Desmontagem](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Iniciar vários processos em uma solução VS, anexar a um processo, iniciar automaticamente um processo no depurador  
  
-   [Inicie vários processos de depuração em uma solução do Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Altere o projeto de inicialização](#BKMK_Change_the_startup_project) • [Inicie um projeto específico em uma solução](#BKMK_Start_a_specific_project_in_a_solution) • [Iniciar projetos múltiplos em uma solução](#BKMK_Start_multiple_projects_in_a_solution) • [Anexar a um processo](#BKMK_Attach_to_a_process) • [Iniciar automaticamente um processo no depurador](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  O depurador não é anexado automaticamente a um processo filho que é inicializado por um processo depurado, mesmo se o projeto filho estiver na mesma solução.  Para depurar um processo filho:  
>   
>  -   Anexar ao processo filho depois que for iniciado.  
>   
>      \-ou\-  
> -   Configurar o Windows para iniciar automaticamente o processo filho em uma nova instância do depurador.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Inicie vários processos de depuração em uma solução do Visual Studio  
 Quando você tiver mais de um projeto em uma solução do Visual Studio que pode executar de forma independente \(projetos que são executados em processos separados\), será possível selecionar quais projetos o depurador inicia.  
  
 ![Alterar o tipo de inicialização para um projeto](~/docs/debugger/media/dbg_execution_startmultipleprojects.png "DBG\_Execution\_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Altere o projeto de inicialização  
 Para alterar o projeto de inicialização de uma solução, selecione o projeto no Solution Explorer e selecione **Definir como projeto de inicialização** do menu de contexto.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Inicie um projeto específico em uma solução  
 Para iniciar um projeto para uma solução sem alterar o projeto de inicialização padrão, selecione o projeto do Gerenciador de Soluções e, em seguida, selecione **Depurar** no menu de contexto.  Você pode escolher **Iniciar nova instância** ou **Depurar completamente a nova instância**.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Iniciar vários processos em uma solução VS, anexar a um processo, iniciar automaticamente um processo no depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Iniciar projetos múltiplos em uma solução  
  
1.  Selecione a solução no Gerenciador de Soluções e depois selecione a solução **Propriedades** no menu de contexto.  
  
2.  Selecione **Propriedades Comuns**, **Projeto de Inicialização** na caixa de diálogo **Propriedades**.  
  
3.  Para cada projeto que você deseja alterar, escolha **Iniciar**, **Iniciar sem Depurar** ou **Nenhum**.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Iniciar vários processos em uma solução VS, anexar a um processo, iniciar automaticamente um processo no depurador](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Anexar a um processo  
 O depurador também pode ser *anexado* a programas que estão sendo executados em processos fora do Visual Studio, incluindo os programas que estão sendo executados em um dispositivo remoto.  Após vincular\-se a um programa, você poderá usar comandos de execução do depurador, inspecionar o estado do programa e assim por diante.  A capacidade de inspecionar o programa pode ser limitada se o programa foi criado com informações de depuração, se você tem acesso ao código\-fonte do programa, e se o compilador just\-in\-time \(JIT\) do Common Language Runtime está controlando as informações de depuração.  
  
 Consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) para obter mais informações.  
  
 **Anexar a um processo que está executando em seu computador local**  
  
 Escolha **Depurar**, **Anexar ao Processo**.  Na caixa de diálogo **Anexar ao Processo**, selecione o processo da lista de **Processos Disponíveis** e, em seguida, escolha **Anexar**.  
  
 ![Anexar a caixa de diálogo do processo](~/docs/debugger/media/dbg_attachtoprocessdlg.png "DBG\_AttachToProcessDlg")  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Iniciar automaticamente um processo no depurador  
 Às vezes, pode ser necessário depurar o código de inicialização para um programa que foi iniciado por outro processo.  Os exemplos incluem serviços e ações de configuração personalizada.  Nesses cenários, você poderá fazer com que o depurador seja iniciado e automaticamente anexado quando seu aplicativo iniciar.  
  
1.  Inicie o Editor do Registro \(**regedit.exe**\).  
  
2.  Navegue até a pasta **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Image File Execution Options**.  
  
3.  Selecione a pasta do aplicativo que você deseja iniciar o depurador.  
  
     Se o nome do aplicativo não estiver listado como uma pasta filha, selecione **Image File Execution Options** e escolha **Novo**, **Chave** no menu de contexto.  Selecione a nova chave, escolha **Renomear** no menu de atalho e digite o nome do aplicativo.  
  
4.  No menu de contexto de pasta de aplicativo, escolha **Novo**, **Valor da Cadeia de Caracteres**.  
  
5.  Altere o nome do novo valor de **New Value** para `depurador`.  
  
6.  No menu de contexto da entrada do depurador, escolha **Modificar**.  
  
7.  Na caixa de diálogo Editar Cadeia de Caracteres, digite `vsjitdebugger.exe` na caixa **Dados de Valor**.  
  
     ![Editar caixa de diálogo String](~/docs/debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG\_Execution\_AutomaticStart\_EditStringDlg")  
  
 ![Depurador automática iniciar entrada em regedit.exe](~/docs/debugger/media/dbg_execution_automaticstart_result.png "DBG\_Execution\_AutomaticStart\_Result")  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Alternar entre processos, interromper e continuar a execução, percorrer origem  
  
-   [Alternar entre processos](#BKMK_Switch_between_processes) • [Interromper, depurar e continuar comandos](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Alternar entre processos  
 Você pode conectar\-se a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento.  Você pode definir o processo ativo *atual* ou na barra de ferramentas do local de depuração ou na janela **Processos**.  Para alternar entre processos, ambos os processos devem estar no modo de interrupção.  
  
 **Para definir o processo atual**  
  
-   Na barra de ferramentas do local de depuração, escolha **Processo** para exibir a caixa de listagem **Processo**.  Selecione o processo que você deseja designar como o processo atual.  
  
     ![Alternar entre processos](~/docs/debugger/media/dbg_execution_switchbetweenmodules.png "DBG\_Execution\_SwitchBetweenModules")  
  
     Se a barra de ferramentas **Local de Depuração** não estiver visível, escolha **Ferramentas**, **Personalizar**.  Na guia **Barras de Ferramentas**, escolha **Local de Depuração**.  
  
-   Abra a janela **Processos** \(atalho **Ctrl\+Alt\+Z**\), localize o processo que você deseja definir como o processo atual e clique duas vezes nele.  
  
     ![Janela de processos](~/docs/debugger/media/dbg_processeswindow.png "DBG\_ProcessesWindow")  
  
     O processo atual é marcado por uma seta amarela.  
  
 Alternar para um projeto o torna o processo atual para fins de depuração.  Qualquer janela do depurador que você exibir mostrará o estado do processo atual e todos os comandos das etapas afetarão somente o processo atual.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Alternar entre processos, interromper e continuar a execução, percorrer origem](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Interromper, depurar e continuar comandos  
  
> [!NOTE]
>  Por padrão, os comandos interromper, continuar e avançar depurador afetam todos os processos que estão sendo depurados.  Para alterar esse comportamento, consulte [Configurar o comportamento de execução de vários processos](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Interromper todos os processos quando um processo for interrompido**<br /><br /> Verificado \(Padrão\)|**Interromper todos os processos quando um processo for interrompido**<br /><br /> Limpo|  
|Menu **Depurar**:<br /><br /> -   **Interromper tudo**|Todos os processos são interrompidos.|Todos os processos são interrompidos.|  
|Menu **Depurar**:<br /><br /> -   **Continue**|Todos os processos são retomados.|Todos os processos suspensos são retomados.|  
|Menu **Depurar**:<br /><br /> -   **Entrar em**<br />-   **Depuração Parcial**<br />-   **Depuração Circular**|Todos os processos estão em execução durante as etapas de processo atual.<br /><br /> Em seguida, todos os processos são interrompidos.|Etapas de processo atual.<br /><br /> Retomada de processos suspensos.<br /><br /> Executando a continuação dos processos.|  
|Menu **Depurar**:<br /><br /> -   **Depurar Completamente o Processo Atual**<br />-   **Depurar de Forma Parcial o Processo Atual**<br />-   **Depurar de Forma Circular o Processo Atual**|N\/D|Etapas de processo atual.<br /><br /> Outros processos mantém o estado existente \(suspenso ou em execução\).|  
|Janela de origem<br /><br /> -   **Ponto de Interrupção**|Todos os processos são interrompidos.|Somente quebras do processo da janela de origem.|  
|Menu de contexto da janela de origem:<br /><br /> -   **Executar até o cursor**<br /><br /> A janela de origem deve estar no processo atual.|Todos os processos estão em execução enquanto o processo da janela de origem executa ao cursor e depois interrompe.<br /><br /> Em seguida, todos os outros processos não interrompidos.|O processo da janela de origem é executado para o cursor.<br /><br /> Outros processos mantém o estado existente \(suspenso ou em execução\).|  
|Menu de contexto da janela **Processos**:<br /><br /> -   **Processo de interrupção**|N\/D|Quebras selecionadas do processo.<br /><br /> Outros processos mantém o estado existente \(suspenso ou em execução\).|  
|Menu de contexto da janela **Processos**:<br /><br /> -   **Continue o processo**|N\/D|O processo selecionado é retomado.<br /><br /> Outros processos mantém o estado existente \(suspenso ou em execução\).|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Alternar entre processos, interromper e continuar a execução, percorrer origem](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Parar a depuração, finalizar ou desanexar dos processos  
  
-   [Parar, finalizar e desanexar comandos](#BKMK_Stop__terminate__and_detach_commands)  
  
 Por padrão, quando você escolhe **Depurar**, **Parar Depuração** quando vários processos estão abertos no depurador, o depurador encerra ou dispara de todos os processos, dependendo de como o processo foi aberto no depurador:  
  
-   Se o processo atual foi iniciado no depurador, esse processo é finalizado.  
  
-   Se você já anexou o depurador ao processo atual, o depurador será desanexado do processo e o deixará em execução.  
  
 Por exemplo, se você iniciar a depuração de um processo de uma solução do Visual Studio, anexá\-lo a outro processo que já esteja em execução e escolher **Parar Depuração**, a sessão de depuração irá parar, o processo que foi iniciado no Visual Studio será finalizado enquanto o processo que você anexou permanecerá em execução.  Você pode usar os seguintes procedimentos para controlar a maneira que você interrompe a depuração.  
  
> [!NOTE]
>  A opção **Interromper todos os processos quando um processo for interrompido** não afeta a interrupção da depuração ou encerramento e desanexação dos processos.  
  
 **Para alterar como a depuração de parada afeta um processo individual**  
  
-   Abra a janela **Processos** \(atalho **Ctrl\+Alt\+Z**\).  Selecione um processo e depois marque ou desmarque a caixa de seleção **Desanexar quando a depuração for interrompida**.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Parar, finalizar e desanexar comandos  
  
|||  
|-|-|  
|**Comando**|**Descrição**|  
|Menu **Depurar**:<br /><br /> -   **Para a depuração**|A menos que o comportamento seja modificado pela opção **Desanexar ao parar a depuração** da janela **Processos**:<br /><br /> 1.  Processos iniciados pelo depurador terminaram.<br />2.  Os processos anexados são separados do depurador.|  
|Menu **Depurar**:<br /><br /> -   **Finalizar Tudo**|Todos os processos são encerrados.|  
|Menu **Depurar**:<br /><br /> -   **Desanexar tudo**|O depurador desanexa todos os processos.|  
|Menu de contexto da janela **Processos**:<br /><br /> -   **Desanexar Processo**|O depurador dispara do processo selecionado.<br /><br /> Outros processos mantém o estado existente \(suspenso ou em execução\).|  
|Menu de contexto da janela **Processos**:<br /><br /> -   **Encerrar Processo**|O processo selecionado é finalizado.<br /><br /> Outros processos mantém o estado existente \(suspenso ou em execução\).|  
|Menu de contexto da janela **Processos**:<br /><br /> -   **Desanexe quando a depuração parar**|Alterna o comportamento de **Depurar**, **Parar Depuração** para o processo selecionado:<br /><br /> -   Verificado: O depurador dispara do processo.<br />-   Limpo: O processo está finalizado.|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Parar a depuração, finalizar ou desanexar dos processos](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
## Consulte também  
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Depuração Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)