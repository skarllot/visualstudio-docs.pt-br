---
title: "Como anexar o criador de perfil a um aplicativo aut&#244;nomo do .NET Framework para coletar dados de mem&#243;ria usando a linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como anexar o criador de perfil a um aplicativo aut&#244;nomo do .NET Framework para coletar dados de mem&#243;ria usando a linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse tópico descreve com usar as [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] Ferramentas de Criação de Perfil da linha de comando para anexar o criador de perfis a um aplicativo independente \(cliente\) em execução do .NET Framework e coletar dados da memória.  
  
> [!NOTE]
>  Ferramentas de linha de comando das Ferramentas de Criação de Perfil estão localizadas no subdiretório \\Team Tools\\Performance Tools do diretório de instalação [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nos computadores de 64 bits, ambas as versões de 64 bits e de 32 bits das ferramentas está disponível.  Para usar as ferramentas de linha de comando do criador de perfis, você deve adicionar o caminho das ferramentas para a variável de ambiente PATH da janela Prompt de Comando ou adicioná\-lo ao próprio comando.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Para anexar a um aplicativo .NET Framework e coletar dados de memória, você deve usar a ferramenta [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) para inicializar as variáveis de ambiente apropriadas antes que o aplicativo de destino seja iniciado.  Quando o criador de perfis é anexado ao aplicativo, é possível usar a ferramenta **VSPerfCmd.exe** para pausar e retomar a coleção de dados.  
  
 Para finalizar uma sessão de criação de perfil, o criador de perfis deve ser desanexado de todos os processos com perfil e o criador de perfis deverá ser explicitamente encerrado.  Na maioria dos casos, recomendamos limpar as variáveis de ambiente ao final de uma sessão.  
  
## Anexando o criador de perfis  
  
#### Para anexar o criador de perfis a um aplicativo do .NET Framework que está em execução  
  
1.  Abra uma janela de prompt de comando.  
  
2.  Inicialize as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfClrEnv** {**\/samplegc** &#124; **\/samplegclife**} \[**\/samplelineoff**\]  
  
    -   As opções **\/samplegc** e **\/samplegclife** especificam se é necessário coletar somente dados de alocação de memória ou coletar dados de alocação de memória e dados tempo de vida do objeto.  Uma e somente uma opção deve ser especificada.  
  
        |Opção|Descrições|  
        |-----------|----------------|  
        |**\/samplegc**|Colete apenas os dados de alocação de memória.|  
        |**\/samplegclife**|Colete dados de tempo de vida do objeto e da alocação de memória.|  
  
    -   A opção **\/samplelineoff** desabilita a coleção de dados de número de linha do código\-fonte.  
  
3.  Inicie o criador de perfis.  Tipo:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   A opção [\/start](../profiling/start.md)**:sample** inicializa o criador de perfis.  
  
    -   A opção [\/output](../profiling/output.md)**:**`OutputFile`é necessária com **\/start** `OutputFile` especifica o nome e o local dos dados de perfil \(.vsp\).  
  
     Você pode usar qualquer uma das seguintes opções com a opção **\/start:sample**.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Especifica o domínio e o nome do usuário da conta que possui o processo com perfil.  Essa opção é necessária somente se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.|  
    |[\/crosssession &#124; \/cs](../profiling/crosssession.md)|Permite analisar os processos em outras sessões.  Essa opção será necessária se o aplicativo estiver sendo executado em uma sessão diferente.  O identificador de sessão é listado na coluna ID da sessão na guia Processos do Windows Task Manager.  **\/CS** pode ser especificado como uma abreviação para **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica o contador de desempenho do Windows que será coletado durante a análise.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Uso com **\/wincounter** somente.  Especifica o número de milissegundos entre eventos de coleção contador de desempenho do Windows.  O padrão é 500 ms.|  
  
4.  Se necessário, inicie o aplicativo de destino normalmente.  
  
5.  Anexa o criador de perfis ao aplicativo de destino.  Tipo:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` especifica o ID do processo do aplicativo de destino.  `ProcessName` especifica o nome do processo.  Observe que se você especificar `ProcessName` e vários processos com o mesmo nome estiverem em execução, os resultados serão imprevisíveis.  Você pode exibir os IDs de processo de todos os processos em execução no Gerenciador de Tarefas do Windows.  
  
    -   **\/targetclr:** `Version` especifica a versão do common language runtime \(CLR\) para analisar quando mais de uma versão do runtime é carregada em um aplicativo.  Opcional.  
  
## Coleta de dados de controle  
 Durante a execução do aplicativo de destino, é possível controlar a coleção de dados iniciando e interrompendo a gravação de dados no arquivo usando as opções de **VSPerfCmd.exe**.  A coleta de dados de controle permite que você colete dados para uma parte específica de execução do programa, como o inicio ou término do aplicativo.  
  
#### Para iniciar e parar a coleção de dados  
  
-   Os seguintes pares de opções iniciam e interrompem a coleção de dados.  Especifique cada opção em uma linha separada de comando.  É possível desativar e ativar a coleção de dados várias vezes.  
  
    |Opção|Descrição|  
    |-----------|---------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Inicia \(**\/globalon**\) ou para \(**\/globaloff**\) a coleção de dados para todos os processos.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Inicia \(**\/processon**\) ou interrompe a coleção de dados \(**\/processoff**\) para o processo especificado pelo `PID`.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** inicia a coleção de dados para o processo especificado pelo `PID` ou pelo nome do processo \(ProcName\).  **\/detach** para a coleta de dados para o processo especificado ou para todos os processos se nenhum processo for especificado.|  
  
## Finalizando a sessão de análise  
 Para finalizar uma sessão de criação de perfil, o criador de perfis deve ser desanexado de todos os processos com perfil e o criador de perfis deverá ser explicitamente encerrado.  Você pode desanexar o criador de perfil de um aplicativo que teve o perfil criado com o método de amostragem fechando o aplicativo ou chamando a opção **VSPerfCmd \/detach**.  Depois, chame a opção **VSPerfCmd \/shutdown** para desativar o criador de perfis e feche o arquivo de dados de criação de perfil.  O comando **VSPerfClrEnv \/off** apaga as variáveis de ambiente de criação de perfis.  
  
#### Para finalizar uma sessão de criação de perfil  
  
1.  Execute uma destas etapas para desanexar o criador de perfis do aplicativo de destino:  
  
    -   Digite **VSPerfCmd \/detach**  
  
         \- ou \-  
  
    -   Feche o aplicativo de destino.  
  
2.  Encerrar o criador de perfis.  Tipo:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Opcional\) Limpe as variáveis do ambiente do perfil.  Tipo:  
  
     **VSPerfCmd \/off**  
  
## Consulte também  
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)