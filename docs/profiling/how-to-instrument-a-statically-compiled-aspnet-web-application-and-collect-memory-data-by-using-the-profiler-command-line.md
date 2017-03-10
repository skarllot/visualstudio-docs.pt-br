---
title: "Como instrumentar um aplicativo Web do ASP.NET compilado estaticamente e coletar dados de mem&#243;ria usando a linha de comando do criador de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como instrumentar um aplicativo Web do ASP.NET compilado estaticamente e coletar dados de mem&#243;ria usando a linha de comando do criador de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para instrumentar um site ou componente Web pré\-compilado do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e coletar alocação de memória .NET, tempo de vida do objeto e dados de intervalo detalhados.  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela prompt de comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para coletar dados de um componente Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando o método de instrumentação, você usa a ferramenta [VSInstr.exe](../profiling/vsinstr.md) para gerar uma versão instrumentada do componente.  No computador que hospeda o componente, você substitui a versão não instrumentada do componente pela versão instrumentada.  Você usa a ferramenta de [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar variáveis de ambiente a globais e para reiniciar o computador host.  Inicie o criador de perfis.  
  
 Durante a execução do componente instrumentado, os dados do tempo são coletados automaticamente em um arquivo de dados.  Você pode pausar e retomar a coleção de dados durante a sessão de criação de perfis.  
  
 Para encerrar uma sessão de criação de perfil, você fecha o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que hospeda o componente e desliga explicitamente o criador de perfil.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Começando a analisar  
  
#### Para instrumentar um componente Web ASP.NET e iniciar a criação de perfil  
  
1.  Use a ferramenta **VSInstr** para gerar uma versão instrumentada do aplicativo de destino.  Se necessário, substitua os binários do aplicativo no computador host do ASP.NET pelos binários instrumentados.  
  
2.  Abra uma janela de prompt de comando  
  
3.  Inicialize as variáveis do ambiente de perfil .NET.  Em uma janela de prompt de comando, digite:  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     \- ou \-  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** coleta dados de tempo e alocação de memória do .NET.  
  
    -   **\/globaltracegclife** coleta dados detalhados de tempo, vida útil do objeto e alocação de memória do .NET.  
  
4.  Reinicie o computador.  
  
5.  Abra uma janela de prompt de comando.  
  
6.  Inicie o criador de perfis.  Em uma janela de prompt de comando, digite:  
  
     **VSPerfCmd \/start:trace \/output:**`OutputFile` \[`Options`\]  
  
    -   A opção [\/start](../profiling/start.md)**:trace** inicializa o criador de perfis.  
  
    -   A opção [\/output](../profiling/output.md)**:**`OutputFile`é necessária com **\/start** `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/start:trace**.  
  
    > [!NOTE]
    >  Geralmente, as opções **\/user** e **\/crosssession** são necessárias para aplicativos do ASP.NET.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio opcional e o nome do usuário da conta que possui o processo de trabalho do ASP.NET.  Essa opção será necessária se o processo estiver sendo executado como um usuário que é diferente do usuário conectado. O nome é listado na coluna Nome de Usuário, na guia Processos do Gerenciador de Tarefas do Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões.  Essa opção será necessária se o aplicativo estiver sendo executado em uma sessão diferente.  A ID da sessão é listada na coluna ID da sessão na guia de processos do gerenciador de tarefas do Windows.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Para iniciar o criador de perfis com a coleção de dados pausada, adicione a opção de **\/globaloff** à linha de comando **\/start**.  Use **\/globalon** para continuar a criação de perfis.|  
  
7.  Abra o site que contém o componente instrumentado.  
  
## Coleta de dados de controle  
 Durante a execução do aplicativo de destino, é possível controlar a coleção de dados iniciando e interrompendo a gravação de dados no arquivo usando as opções de **VSPerfCmd.exe**.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Inicia \(**\/threadon**\) ou interrompe a coleta de dados do thread \(**\/threadoff**\) para o thread especificado por ID de threads \(`TID`\).|  
  
## Finalizando a sessão de análise  
 Para encerrar uma sessão de criação de perfil, feche o aplicativo Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e, em seguida, use o comando **IISReset** do IIS \(Serviços de Informações da Internet\) para fechar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Chame a opção **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) para desativar o criador de perfis e fechar o arquivo de dados de análise.  O comando **VSPerfClrEnv \/globaloff** apaga as variáveis de ambiente de criação de perfis.  Você deve reiniciar o computador para que as novas configurações de ambiente sejam aplicadas.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Feche o aplicativo da Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Feche o processo de trabalho [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Tipo:  
  
     **IISReset \/stop**  
  
3.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
4.  \(Opcional\).  Limpe as variáveis do ambiente de análise.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
5.  Reinicie o computador.  Se necessário, reinicie o IIS.  Tipo:  
  
     **IISReset \/start**  
  
## Consulte também  
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)