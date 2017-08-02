---
title: "Usar arquivos de despejo para depurar falhas e travamentos de aplicativo no Visual Studio | Microsoft Docs"
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
  - "vs.debug.crashdump"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "despejos de memória"
  - "arquivos de despejo"
  - "despejos"
  - "despejos, sobre despejos"
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 53
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usar arquivos de despejo para depurar falhas e travamentos de aplicativo no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Arquivos de despejo com ou sem heaps; crie um arquivo de despejo; abra um arquivo de despejo; localize os binários, os pdbs, e o arquivo de origem para um arquivo de despejo.  
  
##  <a name="BKMK_Contents"></a> Sumário  
 [O que é um arquivo de despejo?](#BKMK_What_is_a_dump_file_)  
  
 [Arquivos de despejo, com ou sem heaps](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Requisitos e restrições](#BKMK_Requirements_and_limitations)  
  
 [Criar um arquivo de despejo.](#BKMK_Create_a_dump_file)  
  
 [Abra um arquivo de despejo.](#BKMK_Open_a_dump_file)  
  
 [Localizar arquivos binários, de símbolo (.pdb), e arquivos de origem](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
##  <a name="BKMK_What_is_a_dump_file_"></a> O que é um arquivo de despejo?  
 Um *arquivo de despejo* é um instantâneo de um aplicativo no momento em que o despejo é realizado.  Mostra que processo estava sendo executado e que módulos foram carregados.  Se o despejo foi salvo com informações de heap, o arquivo de despejo conterá um instantâneo do que estava na memória do aplicativo naquele momento.  Abrir um arquivo de despejo com um heap no Visual Studio é como parar em um ponto de interrupção em uma sessão de depuração.  Embora você não possa continuar a execução, você pode examinar as pilhas, os threads e os valores das variáveis do aplicativo no momento em que o despejo ocorreu.  
  
 Os despejos são usados principalmente para depuração de problemas que ocorrem em máquinas a que o desenvolvedor não tem acesso.  Por exemplo, será possível usar um arquivo de despejo no computador de um cliente quando você não puder reproduzir a pane nem parar o computador.  Os despejos também são criados por testadores para salvar dados de pane ou parada para que o computador de teste possa ser usado para mais testes.  O depurador do Visual Studio pode salvar arquivos de despejo para código gerenciado ou nativo.  O depurador pode carregar arquivos de despejo que foram criados pelo Visual Studio ou por outros programas que salvam arquivos no formato *de minidump* .  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sumário](#BKMK_Contents)  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Arquivos de despejo, com ou sem heaps  
 Você pode criar arquivos de despejo com ou sem informações de heap.  
  
-   **Arquivos de despejo com heaps** contêm um instantâneo da memória do aplicativo.  Isso inclui os valores das variáveis no momento em que o despejo foi criado.  Se você carregar um arquivo de despejo que foi salvo com um heap, o Visual Studio poderá carregar os símbolos, mesmo se o binário do aplicativo não for encontrado.  O Visual Studio também salva os binários nativos dos módulos carregados no arquivo de despejo, o que pode facilitar muito a depuração.  
  
-   **Arquivos de despejo sem heaps** são muito menores do que despejos com informações de heap.  No entanto, o depurador precisa carregar os binários de aplicativo para localizar as informações do símbolo.  Os binários devem ter uma correspondência exata dos binários que foram usados quando o despejo foi criado.  Somente os valores das variáveis de pilha são salvos em arquivos de despejo sem dados do heap.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sumário](#BKMK_Contents)  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Requisitos e restrições  
  
-   Depurar arquivos de despejo de código otimizado pode ser confuso.  Por exemplo, inlining de compilador de funções pode resultar em pilhas de chamadas inesperadas e outras otimizações podem alterar o tempo de vida de variáveis.  
  
-   Os arquivos de despejo de computadores de 64 bits devem ser depurados em uma instância do Visual Studio em execução em um computador de 64 bits.  
  
-   Em versões do Visual Studio anteriores ao VS 2013, os despejos de aplicativos de 32 bits que eram executados em computadores de 64 bits que foram coletados por algumas ferramentas \(como o Gerenciador de Tarefas e o WinDbg de 64 bits\) não podiam ser abertos no Visual Studio.  Essa limitação foi removida do VS 2013.  
  
-   O Visual Studio pode depurar arquivos de despejo de aplicativos nativos de dispositivos ARM.  O Visual Studio também pode depurar arquivos de despejo de aplicativos de gerenciados de dispositivos ARM, mas somente no depurador nativo.  
  
-   Para depurar [modo kernel](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) despejo de arquivos no Visual Studio 2013, baixe o [Windows 8.1 versão das ferramentas de depuração para Windows](http://msdn.microsoft.com/windows/hardware/gg463009).  Consulte [depuração de Kernel no Visual Studio](http://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
-   O Visual Studio não pode depurar arquivos de despejo salvos no formato de despejo mais antigo conhecido como um [despejo completo do modo de usuário](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx).  Observe se um despejo de modo de usuário completo não é igual a um despejo com heap.  
  
-   Para depurar com o [SOS.dll \(Extensão de Depuração SOS\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md) no Visual Studio, você deve instalar as ferramentas de depuração para Windows que faz parte do Windows Driver Kit \(WDK\).  Consulte [Windows 8.1 Preview: Baixe kits, bits e ferramentas](http://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sumário](#BKMK_Contents)  
  
##  <a name="BKMK_Create_a_dump_file"></a> Criar um arquivo de despejo.  
 Para criar um arquivo de despejo com o Visual Studio:  
  
-   Enquanto você estiver depurando um processo no Visual Studio, você pode salvar um arquivo de despejo quando o depurador parar em uma exceção ou em um ponto de interrupção.  Escolha **Salvar Despejo como**, **Depurar**.  Na caixa de diálogo **Salvar Despejo como**, na lista **Salvar como tipo**, você pode selecionar **Minidespejo** ou **Minidespejo com Heap** \(o padrão\).  
  
-   Com [Depuração Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md) habilitado, você pode anexar o depurador a um processo travado que está em execução fora do depurador e salvar um arquivo de despejo.  Consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 Você também pode criar arquivos de despejo com qualquer programa com suporte ao formato minidump do Windows.  Por exemplo, o **Procdump** utilitário de linha de comando do [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) pode criar arquivos de despejo de falha do processo com base em disparadores ou sob demanda.  See [Requisitos e restrições](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) neste tópico para obter informações adicionais sobre como usar outras ferramentas para criar arquivos de despejo.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sumário](#BKMK_Contents)  
  
##  <a name="BKMK_Open_a_dump_file"></a> Abra um arquivo de despejo.  
  
1.  No Visual Studio, escolha **Arquivo**, **Abrir**, **Arquivo**.  
  
2.  Na caixa de diálogo **Abrir Arquivo**, localize e selecione o arquivo de despejo.  Geralmente terá uma extensão .dmp.  Em seguida, escolha **OK**.  
  
3.  A janela de **Resumo de Arquivo de Despejo** aparece.  Nesta janela, você pode exibir informações de resumo de depuração para o arquivo de despejo, definir o caminho do símbolo, iniciar a depuração e copiar as informações de resumo para a área de transferência.  
  
     ![Página de resumo de minidespejo](~/debugger/media/dbg_dump_summarypage.png "DBG\_DUMP\_SummaryPage")  
  
4.  Para iniciar a depuração, vá para o **ações** seção e escolha a opção **Depurar somente com nativo** ou **depurar com misto**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Localizar arquivos binários, de símbolo \(.pdb\), e arquivos de origem  
 Para usar os recursos do Visual Studio para depurar um arquivo de despejo, você precisa de acesso a:  
  
-   O arquivo .exe para o qual o despejo foi feitos e outros binários \(DLLs, etc.\) que foram usados no processo de despejo.  
  
     Se você estiver depurando um despejo com dados da heap, o Visual Studio poderá lidar com os binários ausentes para quaisquer módulos, mas deverá ter binários para módulos suficientes para poder gerar pilhas de chamadas válidas.  O Visual Studio inclui os módulos nativos em um arquivo de despejo com heap.  
  
-   Os arquivos do símbolo \(.pdb\) para o .exe e outros binários.  
  
-   Arquivos de origem para os módulos que você está interessado.  
  
     Os arquivos executável e de .pdb devem corresponder exatamente à versão e a compilação de arquivos usados quando o despejo foi criado.  
  
     Você pode depurar com a desmontagem dos módulos, se não conseguir localizar os arquivos de origem,  
  
 **Caminhos de pesquisa padrão para arquivos executáveis**  
  
 O Visual Studio procura automaticamente nesses locais por arquivos executáveis que não estão incluídos no arquivo de despejo:  
  
1.  O diretório que contém o arquivo de despejo.  
  
2.  O caminho do módulo que é especificado no arquivo de despejo.  Este é o caminho do módulo no computador onde o despejo foi coletado.  
  
3.  Os caminhos de símbolo especificados em **Depuração**, **Opções**, página **Símbolos** do Visual Studio **Ferramentas**, caixa de diálogo **Opções**.  Você pode adicionar mais locais para a pesquisa nessa página.  
  
 **Usando as páginas Não binário\/Símbolo\/Código\-fonte**  
  
 Se o Visual Studio não puder localizar os arquivos necessários para depurar um módulo no despejo, ele exibirá uma página apropriada \(**Nenhum Binário Encontrado**, **Nenhum Símbolo Encontrado** ou **Nenhuma Origem Encontrada**\).  Essas páginas fornecem informações detalhadas sobre a causa do problema e fornecem links de ação que podem ajudá\-lo a identificar o local correto dos arquivos.  Consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sumário](#BKMK_Contents)  
  
## Consulte também  
 [Depuração Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)