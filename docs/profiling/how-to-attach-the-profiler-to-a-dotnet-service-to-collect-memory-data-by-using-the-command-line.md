---
title: "Como anexar o criador de perfil a um servi&#231;o do .NET para coletar dados de mem&#243;ria usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar o criador de perfil a um servi&#231;o do .NET para coletar dados de mem&#243;ria usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil para anexar o profiler para um serviço de  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]e para coletar dados de memória.  Você pode coletar dados sobre o número e o tamanho das alocações de memória, e você também pode coletar dados sobre o tempo de vida de objetos de memória.  
  
> [!NOTE]
>  Os recursos avançados de segurança no Windows 8 e Windows Server 2012 necessitaram de alterações significativas na forma que o profiler do Visual Studio coleta dados dessas plataformas.  Os aplicativos da Windows Store também requerem novas técnicas de coleção.  Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela prompt de comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para coletar dados de memória de um serviço de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], use a ferramenta de [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar as variáveis de ambiente apropriadas no computador que hospeda o serviço.  O computador deve ser reiniciado para configurá\-la para analisar.  
  
 Você usa a ferramenta de [VSPerfCmd](../profiling/vsperfcmd.md) para anexar o profiler para o processo do serviço.  Quando o profiler é anexado ao serviço, você pode pausar e retomar a coleção de dados.  
  
 Para terminar uma sessão, analisando o profiler deverá ser desanexado do serviço e o profiler deverá ser explicitamente fechada.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Anexando o criador de perfis  
  
#### Para anexar o criador de perfis a um serviço do .NET Framework  
  
1.  Se necessário, instale o serviço.  
  
2.  Abra uma janela de prompt de comando.  
  
3.  Inicialize as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv** {**\/globalsamplegc \/globalsamplegclife**}\[**\/samplelineoff**\]  
  
    -   As opções **\/globalsamplegclife** e **\/globalsamplegclife** especificam o tipo de dados de memória para coletar.  Especifique uma e apenas uma das opções a seguir.  
  
     **\/globalsamplegc**  
     Habilita a coleção de dados de alocação de memória.  
  
     **\/globalsamplegclife**  
     Habilita a coleção de dados de alocação de memória e de dados de tempo de vida do objeto.  
  
    -   A opção **\/samplelineoff** desabilita a coleção de dados de número de linha do código\-fonte.  
  
4.  Reiniciar o computador para definir a nova configuração do ambiente.  
  
5.  Se necessário, inicie o serviço.  
  
6.  Abra uma janela de prompt de comando.  Se necessário, adicione o caminho do profiler para a variável de ambiente PATH.  
  
7.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   A opção **\/start:sample** inicializa o criador de perfis.  
  
    -   A opção **\/output:**`OutputFile` é necessária com **\/start**.  `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar uma ou mais das seguintes opções com a opção de **\/start:sample** .  
  
    > [!NOTE]
    >  As opções de **\/user** e de **\/crosssession** geralmente são necessárias para serviços.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome de usuário da conta que possui o processo.  Essa opção é necessária se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões de logon.  Essa opção é necessária se o aplicativo ASP.NET estiver sendo executado em uma sessão diferente.  A ID da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome de usuário opcionais da conta de logon sob a qual o serviço é executado.  A conta de logon é listada no logon como a coluna de serviço no gerenciador de controle de Serviços do Windows.|  
    |[\/crosssession&#124;Cs](../profiling/crosssession.md)|Permite analisar os processos em outras sessões de logon.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
8.  Anexa o criador de perfis ao serviço.  Tipo:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   Especifique a ID de processo ou o nome do processo de serviço.  Você pode exibir os IDs e os nomes de todos os processos em execução no Gerenciador de Tarefas do Windows.  
  
    -   **targetclr:** `Version` especifica a versão do common language runtime \(CLR\) para analisar quando mais de uma versão do runtime é carregada em um aplicativo.  Opcional.  
  
## Coleta de dados de controle  
 Quando o serviço estiver em execução, você pode usar opções de **VSPerfCmd.exe** parar e iniciar a gravação de dados no arquivo de dados do profiler.  A coleta de dados de controle permite coletar dados de uma parte específica de execução do programa, como iniciar ou feche o aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções **VSPerfCmd** iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** inicia a coleção de dados para o processo especificado pelo ID do processo ou nome do processo.  **\/detach** para coleta de dados para o processo especificado, ou para todos os processos se um processo específico não for especificado.|  
  
## Finalizando a sessão de análise  
 Para finalizar uma sessão, o profiler não deve estar coletando dados.  Você pode parar a coleção de dados de um aplicativo analisado com o método de amostragem parando o serviço ou chamando a opção de **VSPerfCmd \/detach** .  Você pode chamar a opção de **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) desativar o profiler e para fechar os dados de perfil arquivo.  O comando **VSPerfClrEnv \/globaloff** limpa todas as variáveis de ambiente, mas a configuração do sistema não é reiniciada até que o computador seja reiniciado.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas opções para desanexar o criador de perfis do aplicativo de destino:  
  
    -   Parar o serviço.  
  
         \- ou \-  
  
    -   Digite **VSPerfCmd \/detach**  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Opcional\) Limpe as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  Reinicie o computador.  
  
## Consulte também  
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)   
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)