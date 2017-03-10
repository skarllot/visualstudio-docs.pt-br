---
title: "Como instrumentar um aplicativo Web do ASP.NET compilado dinamicamente e coletar dados de mem&#243;ria usando a linha de comando do criador de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como instrumentar um aplicativo Web do ASP.NET compilado dinamicamente e coletar dados de mem&#243;ria usando a linha de comando do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil para coletar alocação de memória detalhada de .NET e para o objeto dados de tempo de vida para um aplicativo Web criado dinamicamente de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]usando a instrumentação que analisa o método.  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela prompt de comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para coletar dados de desempenho de um aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , modifique o arquivo web.config do aplicativo de destino habilitar a ferramenta de [VSInstr.exe](../profiling/vsinstr.md) para prover os arquivos de aplicativo criados dinamicamente.  Você usa a ferramenta de [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para configurar o servidor que hospeda o aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e habilita a memória .NET que analisa definindo as variáveis de ambiente apropriadas, e reinicie o computador.  
  
 Para coletar dados, inicie o profiler e execute o aplicativo de destino.  Quando o profiler for anexado ao aplicativo, você pode pausar e retomar a coleta de dados. Quando você coletou os dados apropriados, feche o aplicativo, feche o processo de trabalho do Internet information services \(IIS\), e fecha no profiler.  
  
 Quando você concluiu seu trabalho analisando, restaure o arquivo web.config e o servidor Web para seus estados originais.  
  
## Configurando o aplicativo Web ASP.NET e o servidor Web  
  
#### Para configurar o aplicativo Web ASP.NET e o servidor Web  
  
1.  Modifique o arquivo web.config do aplicativo de destino.  Consulte [Como modificar arquivos Web.Config para instrumentar e criar perfil dinamicamente de aplicativos Web do ASP.NET](../Topic/How%20to:%20Modify%20Web.Config%20Files%20to%20Instrument%20and%20Profile%20Dynamically%20Compiled%20ASP.NET%20Web%20Applications.md).  
  
2.  Abra uma janela de prompt de comando no computador que hospeda o aplicativo Web.  
  
3.  Inicialize as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     \- ou \-  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** habilita a coleção de dados de alocação de memória.  
  
    -   **\/globaltracegclife** habilita a coleção de dados da alocação de memória e de tempo de vida do objeto.  
  
4.  Reinicie o computador.  
  
## Executando a sessão analisando  
  
#### Para analisar o aplicativo Web ASP.NET  
  
1.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd** [\/start](../profiling/start.md) **:trace** [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   A opção **\/start:trace** inicializa o criador de perfis.  
  
    -   A opção **\/output:**`OutputFile` é necessária com **\/start**.  `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/start:trace**.  
  
    > [!NOTE]
    >  Geralmente, as opções **\/user** e **\/crosssession** são necessárias para aplicativos do ASP.NET.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome de usuário opcionais da conta que possui o processo de trabalho de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .  Essa opção é necessária se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O nome é listado na coluna de nome de usuário na guia os processos do gerenciador de tarefas do windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões.  Essa opção será necessária se o aplicativo estiver sendo executado em uma sessão diferente.  A ID da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Inicia o profiler com a coleta de dados pausada.  Use [\/globalon](../profiling/globalon-and-globaloff.md) para continuar analisar.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Coleta informações do contador de desempenho do processador especificado em `Config`.  As informações de contador são adicionadas aos dados coletados em cada evento de perfis.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
2.  Inicie o aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no modo comum.  
  
## Coleta de dados de controle  
 Quando o aplicativo de destino executar, você pode controlar a coleta de dados iniciando e interrompendo a gravação de dados no arquivo de dados do profiler usando opções de **VSPerfCmd.exe** .  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) ou interrompe a coleta de dados do thread \(**\/threadoff**\) para o thread especificado por ID de threads \(`TID`\).|  
  
-   Você também pode usar a opção **VSPerfCmd.exe** [\/mark](../profiling/mark.md) para inserir uma marca no arquivo de dados.  O comando de **\/mark** adiciona um identificador, um carimbo de data\/hora, e uma cadeia de caracteres de texto opcional definida pelo usuário.  As marcas podem ser usadas para filtrar os dados nos relatórios do profiler e em modos de exibição de dados.  
  
## Finalizando a sessão de análise  
 Para terminar uma sessão, analisando feche o aplicativo Web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de destino, interrompa o Internet information services \(IIS\) interromper o processo análise, e feche o profiler.  Reinicie o IIS.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Feche o aplicativo da Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Feche o processo de trabalho de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] redefinindo o Internet information services \(IIS\).  Tipo:  
  
     **IISReset \/stop**  
  
3.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
4.  Reinicie o IIS.  Tipo:  
  
     **IISReset \/start**  
  
## A restauração do aplicativo e a configuração do computador  
 Quando concluir todas analisar, substituir o arquivo web.config, desmarque as variáveis de ambiente, analisando e reiniciar o computador para restaurar o servidor e o aplicativo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]para seus estados originais.  
  
#### Para restaurar o aplicativo e a configuração do computador  
  
1.  Substituir o arquivo web.config com uma cópia do arquivo original.  
  
2.  \(Opcional\).  Limpe as variáveis do ambiente de análise.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
3.  Reinicie o computador.  
  
## Consulte também  
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)