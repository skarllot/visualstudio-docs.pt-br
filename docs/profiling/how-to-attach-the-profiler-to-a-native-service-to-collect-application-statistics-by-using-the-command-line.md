---
title: "Como anexar o criador de perfil a um servi&#231;o nativo para coletar estat&#237;sticas do aplicativo usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar o criador de perfil a um servi&#231;o nativo para coletar estat&#237;sticas do aplicativo usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil para anexar o profiler para um serviço nativo e para coletar estatísticas de desempenho usando o método de amostragem.  
  
> [!NOTE]
>  Os recursos avançados de segurança no Windows 8 e Windows Server 2012 necessitaram de alterações significativas na forma que o profiler do Visual Studio coleta dados dessas plataformas.  Os aplicativos da Windows Store também requerem novas técnicas de coleção.  Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela prompt de comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Quando o profiler é anexado ao serviço, você pode pausar e retomar a coleção de dados.  
  
 Para terminar uma sessão, analisando o profiler deverá ser desanexado do serviço e o profiler deverá ser explicitamente fechada.  
  
## Iniciando o aplicativo com o criador de perfis  
 Para anexar o profiler para um serviço nativo, use **VSPerfCmd.exe**[\/start](../profiling/start.md) e opções de [\/attach](../profiling/attach.md) inicializar o profiler e anexe\-o ao aplicativo de destino.  Você pode especificar **\/start** e **\/attach** e suas respectivas opções em uma única linha de comando.  Você também pode adicionar a opção de [\/globaloff](../profiling/globalon-and-globaloff.md) pausar a coleta de dados no início do aplicativo de destino.  Você pode usar [\/globalon](../profiling/globalon-and-globaloff.md) para começar a coletar dados.  
  
#### Para anexar o criador de perfis a um serviço nativo  
  
1.  Se necessário, inicie o serviço.  
  
2.  Abra uma janela de prompt de comando.  
  
3.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/start:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   A opção **\/start:sample** inicializa o criador de perfis.  
  
    -   A opção **\/output:**`OutputFile` é necessária com **\/start**.  `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/start:sample**.  
  
    > [!NOTE]
    >  As opções de **\/user** e de **\/crosssession** geralmente são necessárias para serviços.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome do usuário da conta que possui o processo com perfil.  Essa opção é necessária somente se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões.  Essa opção será necessária se o aplicativo estiver sendo executado em uma sessão diferente.  A ID da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
4.  Anexa o criador de perfis ao serviço.  Tipo:  
  
     **VSPerfCmd \/attach:** `PID` \[`Sample Event`\]  
  
     `PID` especifica o ID do processo do aplicativo de destino.  Você pode exibir os IDs de processo de todos os processos em execução no Gerenciador de Tarefas do Windows.  
  
     Por padrão, os dados de desempenho são provados a cada 10.000.000 ciclos de relógio não paralisado do processador.  Este é aproximadamente uma vez a cada 10 segundos em um processador 1GH.  Você pode especificar uma das seguintes opções para alterar o intervalo do ciclo de relógio ou especificar um evento diferente da amostragem.  
  
    |Evento de exemplo|Descrição|  
    |-----------------------|---------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Altera o intervalo de amostragem ao número de ciclos de formato não paralisados especificados por `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Altera o evento de amostragem para falhas de página.  Se `Interval` for especificado, ele define o número de falhas de páginas entre as amostras.  O padrão é 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Altera o evento de amostragem para chamadas de sistema do processo para o kernel do sistema operacional \(syscalls\).  Se `Interval` for especificado, ele define o número de chamadas entre as amostras.  O padrão é 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Altera o evento e o intervalo para o contador de desempenho de processador e o intervalo de amostragem especificado em `Config`.|  
  
## Coleta de dados de controle  
 Quando o aplicativo de destino executar, você pode usar opções de **VSPerfCmd.exe** iniciar e interromper a gravação de dados no arquivo de dados do profiler.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções **VSPerfCmd** iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |**\/attach:** {`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** inicia a coleção de dados para o processo especificado pelo ID do processo ou nome do processo.  **\/detach** para coleta de dados para o processo especificado, ou para todos os processos se um processo não é especificado.|  
  
## Finalizando a sessão de análise  
 Para terminar uma sessão, analisando o profiler deverá ser desanexado de serviço e então feche explicitamente.  Você pode desanexar o serviço nativo que está sendo analisado com o método de amostragem parando o serviço ou chamando a opção de **VSPerfCmd \/detach** .  Você pode chamar a opção de **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) desativar o profiler e para fechar os dados de perfil arquivo.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas opções para desanexar o criador de perfis do aplicativo de destino:  
  
    -   Parar o serviço.  
  
         \- ou \-  
  
    -   Digite **VSPerfCmd \/detach**  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
## Consulte também  
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)   
 [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)