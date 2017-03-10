---
title: "Como instrumentar um servi&#231;o do .NET e coletar dados de tempo detalhados usando a linha de comando do criador de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como instrumentar um servi&#231;o do .NET e coletar dados de tempo detalhados usando a linha de comando do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse tópico descreve como usar as Ferramentas de Criação de Perfil da linha de comando [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] para instrumentar um serviço do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e coletar dados detalhados do tempo.  
  
> [!NOTE]
>  Não é possível analisar um serviço com o método de instrumentação se o serviço não puder ser reiniciado após a inicialização do computador, como um serviço que é iniciado apenas quando o sistema operacional é inicializado.  
>   
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela prompt de comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  A adição de dados de interação da camada à execução de criação de perfil requer procedimentos específicos com ferramentas de criação de perfil de linha de comando.  Consulte [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Para coletar dados de intervalo detalhados de um serviço [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usando o método de instrumentação, você usa a ferramenta [VSInstr.exe](../profiling/vsinstr.md) para gerar uma versão instrumentada do componente.  Você substitui a versão não instrumentada do serviço com a versão instrumentada, certificando\-se que o serviço está configurado para iniciar manualmente.  Você usa a ferramenta de [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar variáveis de ambiente a globais e reiniciar o computador host.  Inicie o criador de perfis.  
  
 Quando o serviço é iniciado, os dados de tempo são coletados automaticamente em um arquivo de dados.  Você pode pausar e retomar a coleção de dados durante a sessão de criação de perfis.  
  
 Para encerrar uma sessão de criação de perfil, desative o serviço e desligue explicitamente o criador de perfis.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Iniciando o aplicativo com o criador de perfis  
  
#### Para iniciar a análise de um serviço do .NET Framework  
  
1.  Abra uma janela de prompt de comando.  
  
2.  Use a ferramenta **VSInstr** para gerar uma versão provida de binário de serviço.  
  
3.  Substitua o binário original pela versão instrumentada.  No Gerenciador de Controle de Serviço do Windows, certifique\-se de que o tipo de inicialização de serviço esteja definido para manual.  
  
4.  Inicialize as variáveis do ambiente de perfil [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Tipo:  
  
     **VSPerfClrEnv \/globaltraceon**  
  
5.  Reinicie o computador.  
  
6.  Abra uma janela de prompt de comando.  
  
7.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   A opção [\/start](../profiling/start.md)**:trace** inicializa o criador de perfis.  
  
    -   A opção [\/output](../profiling/output.md)**:**`OutputFile`é necessária com **\/start** `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     É possível usar uma das seguintes opções com a opção **\/start:trace**.  
  
    > [!NOTE]
    >  Geralmente, as opções **\/user** e de **\/crosssession** são necessárias para serviços de análise.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome do usuário da conta que possui o processo com perfil.  Essa opção é necessária somente se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões.  Essa opção será necessária se o aplicativo estiver sendo executado em uma sessão diferente.  A ID da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Especifica o número de segundos para esperar pelo profiler inicializar antes que ele retorne um erro.  Se `Interval` não for especificado, o criador de perfis aguardará indefinidamente.  Por padrão, **\/start** retorna imediatamente.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Para iniciar o criador de perfis com a coleção de dados pausada, adicione a opção de **\/globaloff** à linha de comando **\/start**.  Use **\/globalon** para continuar a criação de perfis.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Coleta informações do contador de desempenho do processador especificado na configuração.  As informações de contador são adicionadas aos dados coletados em cada evento de perfis.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
8.  Inicie o serviço do Gerenciador de Controle de Serviço do Windows.  
  
## Coleta de dados de controle  
 Durante a execução do serviço, é possível usar as opções de **VSPerfCmd.exe** para iniciar e parar a gravação de dados no arquivo de dados do criador de perfis.  A coleção de dados de controle permite que você colete dados para uma parte específica de execução do programa, como início ou encerramento do serviço.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções **VSPerfCmd** iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) ou interrompe a coleta de dados do thread \(**\/threadoff**\) para o thread especificado por ID de threads \(`TID`\).|  
  
## Finalizando a sessão de análise  
 Para encerrar uma sessão de criação de perfil, pare o serviço que está executando o componente instrumentado e chame a opção **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desativar o criador de perfis e feche o arquivo de dados de criação de perfil.  O comando **VSPerfClrEnv \/globaloff** apaga as variáveis de ambiente de criação de perfis.  
  
 Você deve reiniciar o computador para que as novas configurações de ambiente sejam aplicadas.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Interromper o serviço do Gerenciador de Controle de Serviços.  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  Quando você tiver concluído todas as criações de perfil, desmarque as variáveis de ambiente de criação de perfil.  Tipo:  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  Substitua o módulo instrumentado pelo original.  Se necessário, reconfigure o tipo de inicialização do serviço.  
  
5.  Reinicie o computador.  
  
## Consulte também  
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)   
 [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)