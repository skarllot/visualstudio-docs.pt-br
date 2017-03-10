---
title: "Como anexar o criador de perfil a um aplicativo Web ASP.NET para coletar dados de mem&#243;ria usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar o criador de perfil a um aplicativo Web ASP.NET para coletar dados de mem&#243;ria usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil para anexar o profiler para um aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e para coletar dados sobre o número e o tamanho de alocações de memória do.NET Framework.  Você também pode coletar dados sobre o tempo de vida de objetos de memória do.NET Framework.  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela Prompt de Comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para coletar dados de desempenho de um aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , você deve usar a ferramenta de [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar as variáveis de ambiente apropriadas no computador que hospeda o aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  Você deve reiniciar o computador para configurar o servidor da Web para analisar.  
  
 Você usa a ferramenta de [VSPerfCmd.exe](../profiling/vsperfcmd.md) para anexar o profiler para o processo de trabalho de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]que hospeda o site.  Quando o profiler é anexado ao aplicativo, você pode pausar e retomar a coleção de dados.  
  
 Para encerrar uma sessão de criação de perfil, o criador de perfis não deve mais estar anexado ao aplicativo, e deverá ser explicitamente desligado.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Anexando o criador de perfis  
  
#### Para anexar o criador de perfis a um aplicativo Web ASP.NET  
  
1.  Abra uma janela de prompt de comando.  
  
2.  Inicialize as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   As opções **\/globalsamplegc** e **\/globalsamplegclife** especificam o tipo de dados de memória para coletar.  
  
         Especifique uma e apenas uma das opções a seguir.  
  
        |Opção|Descrição|  
        |-----------|---------------|  
        |**\/globalsamplegc**|Habilita a coleção de dados de alocação de memória.|  
        |**\/globalsamplegclife**|Habilita a coleção de dados de alocação de memória e de dados de tempo de vida do objeto.|  
  
    -   A opção **\/samplelineoff** desabilita a atribuição de dados coletados nas linhas específicas do código\-fonte.  Se essa opção for especificada, os dados serão atribuídas à função.  
  
3.  Reiniciar o computador para definir a nova configuração do ambiente.  
  
4.  Abra uma janela de prompt de comando.  Se necessário, defina a variável de ambiente do caminho do profiler.  
  
5.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   A opção **\/start:sample** inicializa o criador de perfis.  
  
    -   A opção **\/output:**`OutputFile` é necessária com **\/start**.  `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/start:sample**.  
  
    > [!NOTE]
    >  Geralmente, as opções **\/user** e **\/crosssession** são necessárias para aplicativos do ASP.NET.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome do usuário da conta que possui o processo de trabalho do ASP.NET.  Essa opção será necessária se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões de logon.  Essa opção é necessária se o aplicativo ASP.NET estiver sendo executado em uma sessão diferente.  A identificação da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|Especifica o número de segundos para esperar pelo profiler inicializar antes que ele retorne um erro.  Se `Interval` não for especificado, o criador de perfis aguardará indefinidamente.  Por padrão, **\/start** retorna imediatamente.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
6.  Inicie o aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no modo comum.  
  
7.  Anexe o profiler para o processo de trabalho de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  Tipo:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   A ID de processo `(PID)` especifica a ID de processo ou o nome do processo de trabalho de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  Você pode exibir os IDs de processo de todos os processos em execução no Gerenciador de Tarefas do Windows.  
  
    -   **\/targetclr:** `Version` especifica a versão do Common Language Runtime \(CLR\) para analisar quando mais de uma versão de tempo de execução é carregada em um aplicativo.  
  
## Coleta de dados de controle  
 Quando o aplicativo execute, você pode controlar a coleta de dados iniciando e interrompendo a gravação de dados no arquivo de dados do profiler usando opções de **VSPerfCmd.exe** .  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções **VSPerfCmd** iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia**\/processon**\(\) ou coleta de dados de para \(**\/processoff**\) para o processo especificado por `PID`.|  
    |**\/attach:**{`PID`&#124;`ProcName`[\/detach](../profiling/detach.md)**:**{} \[`PID`&#124;:`ProcName`}\]|início de**\/attach** para coletar dados para o processo que é especificado pelo nome de identificação do processo ou do processo.  **\/detach** para a coleta de dados para o processo especificado ou para todos os processos se nenhum processo for especificado.|  
  
## Finalizando a sessão de análise  
 Para terminar uma sessão, analisando o profiler deverá ser desanexado do aplicativo Web.  Você pode parar a coleção de dados de um aplicativo que foi analisado com o método de amostragem reiniciar o processo de trabalho de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ou chamando a opção de **VSPerfCmd \/detach**.  Você pode chamar a opção de **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) desativar o profiler e para fechar os dados de perfil arquivo.  O comando **VSPerfClrEnv \/globaloff** limpa todas as variáveis de ambiente, mas a configuração do sistema não é reiniciada até que o computador seja reiniciado.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas etapas para desanexar o criador de perfis do aplicativo de destino:  
  
    -   Tipo **VSPerfCmd** [\/detach](../profiling/detach.md)  
  
         \- ou \-  
  
    -   Feche o processo de trabalho [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Tipo:  
  
     **IISReset \/stop**  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Opcional\) Limpe as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
4.  Reinicie o computador.  Se necessário, reinicie o Internet information services \(IIS\).  Tipo:  
  
     **IISReset \/start**  
  
## Consulte também  
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)