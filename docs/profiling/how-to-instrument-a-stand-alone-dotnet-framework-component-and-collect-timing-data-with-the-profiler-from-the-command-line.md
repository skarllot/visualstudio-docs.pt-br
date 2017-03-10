---
title: "Como instrumentar um componente do .NET Framework aut&#244;nomo e coletar dados de tempo com o criador de perfil a partir da linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como instrumentar um componente do .NET Framework aut&#244;nomo e coletar dados de tempo com o criador de perfil a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil para prover um componente do.NET Framework como um arquivo ou o arquivo .dll, e para coletar dados de controle de tempo detalhado.  
  
> [!NOTE]
>  Os recursos avançados de segurança no Windows 8 e Windows Server 2012 necessitaram de alterações significativas na forma que o profiler do Visual Studio coleta dados dessas plataformas.  Os aplicativos da Windows Store também requerem novas técnicas de coleção.  Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela Prompt de Comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  A adição de dados de interação da camada à execução de criação de perfil requer procedimentos específicos com ferramentas de criação de perfil de linha de comando.  Consulte [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Para coletar dados de controle de tempo detalhado de um componente do.NET Framework usando o método de gerenciamento, use a ferramenta de [VSInstr.exe](../profiling/vsinstr.md) para gerar uma versão instrumentada do componente e da ferramenta de [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar analisar as variáveis de ambiente.  Inicie o criador de perfis.  
  
 Durante a execução do componente instrumentado, os dados do tempo são coletados automaticamente em um arquivo de dados.  Você pode pausar e retomar a coleção de dados durante a sessão de criação de perfis.  
  
 Para terminar uma sessão, analisando você fecha o aplicativo de destino e feche explicitamente o profiler.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Iniciando a sessão de análise  
  
#### Para iniciar a análise usando o método de gerenciamento  
  
1.  Abra uma janela de prompt de comando.  Se necessário, adicione o diretório de ferramentas do profiler a sua variável de ambiente PATH.  O caminho não é adicionado à instalação.  
  
2.  Use a ferramenta **VSInstr** para gerar uma versão instrumentada do aplicativo de destino.  
  
3.  Inicializar o.NET Framework que analisa as variáveis de ambiente.  Tipo:  
  
     **VSPerfClrEnv \/traceon**  
  
4.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   A opção [\/start](../profiling/start.md)**:trace** inicializa o criador de perfis.  
  
    -   A opção [\/output](../profiling/output.md)**:**`OutputFile`é necessária com **\/start** `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     É possível usar uma das seguintes opções com a opção **\/start:trace**.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome do usuário da conta que possui o processo com perfil.  Essa opção é necessária somente se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões.  Essa opção é necessária se o aplicativo ASP.NET estiver sendo executado em uma sessão diferente.  A identificação da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Inicia o profiler com a coleta de dados pausada.  Use [\/globalon](../profiling/globalon-and-globaloff.md) para continuar analisar.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Coleta informações do contador de desempenho de processador que é especificado em `Config`.  As informações do contador é adicionado aos dados coletados em cada evento analisando.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
5.  Inicie o aplicativo de destino na janela prompt de comando.  
  
## Coleta de dados de controle  
 Durante a execução do aplicativo de destino, é possível controlar a coleção de dados iniciando e interrompendo a gravação de dados no arquivo de dados do criador de perfis usando as opções de **VSPerfCmd.exe**.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) ou interrompe a coleta de dados do thread \(**\/threadoff**\) para o thread especificado por ID de threads \(`TID`\).|  
  
## Finalizando a sessão de análise  
 Para terminar uma sessão, analisando feche o aplicativo que está executando o componente provido.  Chame a opção **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desativar o criador de perfis e fechar o arquivo de dados de análise.  O comando **VSPerfClrEnv \/off** apaga as variáveis de ambiente de criação de perfis.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Feche o aplicativo de destino.  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Opcional\) Limpe as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv \/off**  
  
## Consulte também  
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)