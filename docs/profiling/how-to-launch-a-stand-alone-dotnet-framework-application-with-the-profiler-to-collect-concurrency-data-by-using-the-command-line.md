---
title: "Como iniciar um aplicativo do .NET Framework aut&#244;nomo com o criador de perfil para coletar dados de simultaneidade usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como iniciar um aplicativo do .NET Framework aut&#244;nomo com o criador de perfil para coletar dados de simultaneidade usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como usar as ferramentas de linha de comando de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil para iniciar um aplicativo autônomo do .NET Framework \(cliente\) e para coletar dados de simultaneidade do processo e do thread  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela prompt de comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Quando o profiler é anexado ao aplicativo, você pode pausar e retomar a coleção de dados.  Para finalizar uma sessão, o Criador de Perfis não deve estar anexado ao aplicativo, e deve ser explicitamente fechado.  
  
## Iniciando o aplicativo com o criador de perfis  
 Para iniciar um aplicativo de destino do.NET Framework com o profiler, você usa VSPerfClrEnv.exe para definir o.NET Framework que analisa variáveis.  Você usa o VSPerfCmd **\/start** e opções de **\/launch** inicializar o profiler e iniciar o aplicativo.  Você pode especificar **\/start** e **\/launch** e suas respectivas opções em uma única linha de comando.  Você também pode adicionar a opção de **\/globaloff** à linha de comando à coleta de dados de pausa quando o aplicativo de destino.  Você usa **\/globalon** em uma linha de comando separadamente para começar a coletar dados.  
  
#### Para iniciar um aplicativo com o profiler  
  
1.  Abra uma janela de prompt de comando.  
  
2.  Inicie o criador de perfis.  Tipo:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   A opção de [\/start](../profiling/start.md) inicializa o profiler.  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|Permite coletar a contenção de recursos e os dados de execução de thread.|  
        |**\/start:concurrency,resourceonly**|Permite coletar apenas dados de contenção de recursos.|  
        |**\/start:concurrency,threadonly**|Permite coletar apenas dados de execução de thread.|  
  
    -   A opção [\/output](../profiling/output.md)**:**`OutputFile`é necessária com **\/start** `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/start:concurrency** .  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Especifica o domínio e o nome da conta de usuário opcionais para ter acesso concedido ao profiler.|  
    |[\/crosssession](../profiling/crosssession.md)|Permite analisar os processos em outras sessões de logon.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica um rastreamento de evento para evento do Windows \(ETW\) para ser coletado durante a análise.  Os eventos de ETW são coletados em um arquivo separado \(.etl\).|  
  
3.  Inicie o aplicativo de destino.  Tipo:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` `Options`\[\] \[`Sample Event`\]  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/launch**.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Especifica uma cadeia de caracteres que contém argumentos de linha de comando a ser passado para o aplicativo de destino.|  
    |[\/console](../profiling/console.md)|Inicia o aplicativo de linha de comando de destino em uma janela separada.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Especifica a versão do Common Language Runtime \(CLR\) para analisar quando mais de uma versão do tempo de execução é carregada em um aplicativo.|  
  
## Coleta de dados de controle  
 Quando o aplicativo destino é executado, você pode controlar a coleção de dados iniciando e parando a escrita de dados para o arquivo usando opções de VSPerfCmd.exe.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
1.  Os seguintes pares de opções VSPerfCmd.exe começam e param a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleta de dados \(**\/processoff**\) para o processo especificado pelo ID de processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia a coleção de dados para o processo especificado pelo ID do processo \(`PID`\) ou nome do processo \(ProcName\).  **\/detach** para a coleta de dados para o processo especificado ou para todos os processos se nenhum processo for especificado.|  
  
## Finalizando a sessão de análise  
 Para finalizar uma sessão, o profiler não deve estar coletando dados.  Você pode interromper a coleta de dados de simultaneidade fechando o aplicativo analisado ou invocando a opção de **VSPerfCmd \/detach** .  Então, você chama a opção **VSPerfCmd \/shutdown** para desativar o criador de perfis e fechar o arquivo de dados de criação de perfil.  O comando **VSPerfClrEnv \/off** apaga as variáveis de ambiente de criação de perfis.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas opções para desanexar o criador de perfis do aplicativo de destino.  
  
    -   Feche o aplicativo de destino.  
  
         \- ou \-  
  
    -   Digite **VSPerfCmd \/detach**  
  
2.  Feche o profiler  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Consulte também  
 [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)