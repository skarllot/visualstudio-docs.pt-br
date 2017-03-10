---
title: "Como anexar o criador de perfil a um aplicativo Web ASP.NET para coletar estat&#237;sticas de aplicativo usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar o criador de perfil a um aplicativo Web ASP.NET para coletar estat&#237;sticas de aplicativo usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse tópico descreve como usar as Ferramentas de Criação de Perfil da linha de comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para anexar o criador de perfis a um aplicativo Web ASP.NET e coletar as estatísticas de desempenho usando o método de amostragem.  
  
> [!NOTE]
>  Os recursos avançados de segurança no Windows 8 e Windows Server 2012 necessitaram de alterações significativas na forma que o profiler do Visual Studio coleta dados dessas plataformas.  Os aplicativos da Windows Store também requerem novas técnicas de coleção.  Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  A adição de dados de interação da camada à execução de criação de perfil requer procedimentos específicos com ferramentas de criação de perfil de linha de comando.  Consulte [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas à variável de ambiente PATH da janela de Prompt de Comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para coletar dados de desempenho de um aplicativo Web ASP.NET, as variáveis de ambiente apropriadas devem ser inicializadas e o computador que hospeda o aplicativo Web ASP.NET deve ser reiniciado para configurar o servidor Web para criação de perfil.  
  
 Em seguida, anexe o criador de perfis ao processo de trabalho do ASP.NET que hospeda o site.  Quando o profiler é anexado ao aplicativo, você pode pausar e retomar a coleção de dados.  
  
 Para encerrar uma sessão de criação de perfil, o criador de perfis deve ser desanexado do aplicativo analisado e o criador de perfis deverá ser explicitamente desligado.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Iniciando o criador de perfis e anexando a um aplicativo Web ASP.NET  
  
#### Para anexar o criador de perfis a um aplicativo Web ASP.NET  
  
1.  Abra uma janela de prompt de comando.  
  
2.  Inicialize as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv \/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** permite a amostragem.  
  
    -   **\/samplelineoff** desativa a atribuição de dados coletados a linhas de código específicas da fonte.  Quando essa opção é especificada, os dados são atribuídos somente a funções.  
  
3.  Reinicie o computador.  
  
4.  Inicie o criador de perfis.  Tipo:**VSPerfCmd** [\/start](../profiling/start.md)**:sample** [\/output](../profiling/output.md)**:**`OutputFile`\[`Options`\]  
  
    -   A opção **\/start:sample** inicializa o criador de perfis.  
  
    -   A opção **\/output:**`OutputFile` é necessária com **\/start**.  `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     É possível usar uma das seguintes opções com a opção **\/start:sample**.  
  
    > [!NOTE]
    >  Geralmente, as opções **\/user** e **\/crosssession** são necessárias para aplicativos do ASP.NET.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome do usuário da conta que possui o processo de trabalho do ASP.NET.  Essa opção será necessária se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões de logon.  Essa opção é necessária se o aplicativo ASP.NET estiver sendo executado em uma sessão diferente.  A identificação da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
5.  Inicie o aplicativo da Web ASP.NET de maneira normal.  
  
6.  Anexe o criador de perfis ao processo de trabalho do ASP.NET.  Tipo:**VSPerfCmd** [\/attach](../profiling/attach.md)**:**{`PID` &#124;`ProcName`} \[`Sample Event`\] \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` especifica a identificação do processo do processo de trabalho do ASP.NET; `ProcName` especifica o nome do processo de trabalho.  Você pode exibir os IDs e os nomes de todos os processos em execução no Gerenciador de Tarefas do Windows.  
  
    -   Por padrão, os dados de desempenho são provados a cada 10.000.000 ciclos de relógio não paralisado do processador.  É cerca de 100 vezes por segundo em um processador de 1 GH.  É possível especificar uma das seguintes opções de **VSPerfCmd** para alterar o intervalo de ciclo de relógio ou especificar um evento de amostragem diferente.  
  
    |Evento de exemplo|Descrição|  
    |-----------------------|---------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Altera o intervalo de amostragem para o número de ciclos de relógio não paralisados especificados por `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Altera o evento de amostragem para falhas de página.  Se `Interval` for especificado, ele define o número de falhas de páginas entre as amostras.  O padrão é 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[`:``Interval`\]|Altera o evento de amostragem para chamadas de sistema do processo para o kernel do sistema operacional \(syscalls\).  Se `Interval` for especificado, ele define o número de chamadas entre as amostras.  O padrão é 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Altera o evento de amostragem e o intervalo para o contador de desempenho do processador e o intervalo que são especificados em `Config`.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Especifica a versão do Common Language Runtime \(CLR\) para analisar quando mais de uma versão do tempo de execução é carregada em um aplicativo.|  
  
    -   **targetclr:** `Version` especifica a versão do CLR para analisar quando mais de uma versão do tempo de execução é carregada em um aplicativo.  Opcional.  
  
## Coleta de dados de controle  
 Durante a execução do aplicativo, é possível controlar a coleção de dados iniciando e interrompendo a gravação de dados no arquivo usando as opções de **VSPerfCmd.exe**.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções **VSPerfCmd** iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` **\/processoff:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleção de dados \(**\/processoff**\) para o processo especificado pelo `PID`.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia a coleção de dados para o processo especificado pelo `PID` ou pelo nome do processo \(ProcName\).  **\/detach** para a coleta de dados para o processo especificado ou para todos os processos se nenhum processo for especificado.|  
  
## Finalizando a sessão de análise  
 Para encerrar uma sessão de criação de perfil, feche o aplicativo Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e, em seguida, use o comando **IISReset** do IIS \(Serviços de Informações da Internet\) para fechar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Chame a opção **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desativar o criador de perfis e fechar o arquivo de dados de análise.  
  
 O comando **VSPerfClrEnv \/globaloff** apaga as variáveis de ambiente de criação de perfis.  Você deve reiniciar o computador para que as novas configurações de ambiente sejam aplicadas.  
  
 O comando **VSPerfClrEnv \/globaloff** limpa todas as variáveis de ambiente, mas a configuração do sistema não é reiniciada até que o computador seja reiniciado.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas opções para desanexar o criador de perfis do aplicativo de destino:  
  
    -   Digite **VSPerfCmd \/detach**  
  
         \- ou \-  
  
    -   Feche o processo de trabalho [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Encerrar o criador de perfis.  Tipo:**VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Opcional\) Limpe as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
4.  Reinicie o computador.  
  
## Consulte também  
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)