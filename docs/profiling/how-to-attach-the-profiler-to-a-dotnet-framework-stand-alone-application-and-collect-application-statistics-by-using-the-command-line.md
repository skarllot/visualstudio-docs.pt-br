---
title: "Como anexar o criador de perfil a um aplicativo aut&#244;nomo do .NET Framework e coletar estat&#237;sticas de aplicativo usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar o criador de perfil a um aplicativo aut&#244;nomo do .NET Framework e coletar estat&#237;sticas de aplicativo usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse tópico descreve como usar as Ferramentas de Criação de Perfil da linha de comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para anexar o criador de perfis a um aplicativo autônomo nativo em execução \(cliente\) do .NET Framework e coletar as estatísticas de desempenho usando o método de amostragem.  
  
> [!NOTE]
>  Os recursos avançados de segurança no Windows 8 e Windows Server 2012 necessitaram de alterações significativas na forma que o profiler do Visual Studio coleta dados dessas plataformas.  Os aplicativos da Windows Store também requerem novas técnicas de coleção.  Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela Prompt de Comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  A adição de dados de interação da camada à execução de criação de perfil requer procedimentos específicos com ferramentas de criação de perfil de linha de comando.  Consulte [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Para coletar dados de desempenho de um aplicativo .NET Framework, as variáveis de ambiente apropriadas devem ser inicializadas antes que o aplicativo de destino seja iniciado.  Quando o profiler é anexado ao aplicativo, você pode pausar e retomar a coleção de dados.  
  
 Para encerrar uma sessão de criação de perfil, o criador de perfis não deve mais estar anexado ao aplicativo, e deverá ser explicitamente desligado.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente de análise no final de uma sessão de análise.  
  
## Anexando o criador de perfis  
  
#### Para anexar o criador de perfis a um aplicativo do .NET Framework que está em execução  
  
1.  Abra uma janela de prompt de comando.  
  
2.  Inicialize as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv \/sampleon** \[**\/samplelineoff**\]  
  
    -   A opção **\/samplelineoff** desabilita a coleção de dados de número de linha do código\-fonte.  
  
3.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   A opção [\/start](../profiling/start.md)**:sample** inicializa o criador de perfis.  
  
    -   A opção [\/output](../profiling/output.md)**:**`OutputFile`é necessária com **\/start** `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     É possível usar uma das seguintes opções com a opção **\/start:sample**.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio opcional e o nome do usuário da conta que possui o processo analisado.  Essa opção só será necessária se o aplicativo analisado tiver sido iniciado como um usuário diferente do usuário conectado.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões de logon.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.  Essa opção será necessária se o aplicativo estiver sendo executado em uma sessão diferente.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
4.  Se necessário, inicie o aplicativo de destino normalmente.  
  
5.  Anexa o criador de perfis ao aplicativo de destino.  Tipo:  
  
     **VSPerfCmd \/attach:**{`PID`&#124;`ProcessName`} \[`Sample Event`\] \[**\/targetclr:**`Version`\]  
  
    -   `PID` especifica o ID do processo do aplicativo de destino.  `ProcessName` especifica o nome do processo.  Observe que se você especificar `ProcessName` e vários processos com o mesmo nome estiverem em execução, os resultados serão imprevisíveis.  Você pode exibir os IDs de processo de todos os processos em execução no Gerenciador de Tarefas do Windows.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` especifica a versão do common language runtime \(CLR\) para analisar quando mais de uma versão do runtime é carregada em um aplicativo.  Opcional.  
  
    -   Por padrão, os dados de desempenho são provados a cada 10.000.000 ciclos de relógio não paralisado do processador.  É cerca de uma vez a cada 10 segundos em um processador de 1 GH.  É possível especificar uma das seguintes opções para alterar o intervalo de ciclo de relógio ou especificar um evento de amostragem diferente.[\/targetclr](../profiling/targetclr.md)**:**`Version` especifica a versão do CLR para analisar quando mais de uma versão do tempo de execução é carregada em um aplicativo.  Opcional.  
  
    |||  
    |-|-|  
    |Evento de exemplo|Descrição|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Altera o intervalo de amostragem para o número de ciclos de relógio não paralisados especificados por `Interval`.|  
    |[\/pf](../profiling/pf.md) \[**:**`Interval`\]|Altera o evento de amostragem para falhas de página.  Se `Interval` for especificado, ele define o número de falhas de páginas entre as amostras.  O padrão é 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Altera o evento de amostragem para chamadas de sistema do processo para o kernel do sistema operacional \(syscalls\).  Se `Interval` for especificado, ele define o número de chamadas entre as amostras.  O padrão é 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Altera o evento de amostragem e o intervalo para o contador de desempenho do processador e o intervalo que são especificados em `Config`.|  
  
## Coleta de dados de controle  
 Durante a execução do aplicativo de destino, é possível controlar a coleção de dados iniciando e interrompendo a gravação de dados no arquivo de dados do criador de perfis usando as opções de **VSPerfCmd.exe**.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleção de dados \(**\/processoff**\) para o processo especificado pelo `PID`.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia a coleção de dados para o processo especificado pelo `PID` ou pelo nome do processo \(ProcName\).  **\/detach** para a coleta de dados para o processo especificado ou para todos os processos se nenhum processo for especificado.|  
  
## Finalizando a sessão de análise  
 Para finalizar uma sessão de criação de perfil, o criador de perfis deve ser desanexado de todos os processos com perfil e o criador de perfis deverá ser explicitamente encerrado.  Você pode desanexar o criador de perfil de um aplicativo que teve o perfil criado com o método de amostragem fechando o aplicativo ou chamando a opção **VSPerfCmd \/detach**.  Então, você chama a opção **VSPerfCmd \/shutdown** para desativar o criador de perfis e fechar o arquivo de dados de criação de perfil.  O comando **VSPerfClrEnv \/off** apaga as variáveis de ambiente de criação de perfis.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas etapas para desanexar o criador de perfis do aplicativo de destino:  
  
    -   Digite **VSPerfCmd \/detach**  
  
         \- ou \-  
  
    -   Feche o aplicativo de destino.  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Opcional\) Limpe as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv \/off**  
  
## Consulte também  
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)