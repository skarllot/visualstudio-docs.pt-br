---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "linha de comando, ferramentas"
  - "ferramentas de linha de comando, Ferramenta VSPerfCmd"
  - "ferramentas de desempenho, Ferramenta VSPerfCmd"
  - "ferramentas de criação de perfil, VSPerfCmd"
  - "Ferramenta VSPerfCmd"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A ferramenta de **VSPerfCmd.exe** é usada para iniciar e interromper a coleta de dados de desempenho.  Use a seguinte sintaxe:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 As tabelas a seguir descrevem opções da ferramenta de **VSPerfCmd.exe** .  
  
|Opção|Descrição|  
|-----------|---------------|  
|**U**|A saída redirecionada de console são gravadas como Unicode.  Deve ser a primeira opção especificada.|  
|[Iniciar](../profiling/start.md) **:** `mode`|Inicia o serviço analisando no modo especificado.|  
|[Saída](../profiling/output.md) **:** `filename`|Especifica o nome do arquivo de saída.  Use apenas com **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Permite analisar em sessões do windows.  Use apenas com **Start**, **Attach**, **or Launch**.|  
|[Usuário](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Habilita o acesso especificado da conta para o serviço do profiler.  Use apenas com **Start**.|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|Espera para que o agente de coleta de dados inicialize.  Se `n` for especificado, **VSPerfCmd** aguardará no máximo de segundos `n` .  Se `n` não for especificado, **VSPerfCmd** aguardará indefinidamente.  Isso facilita o uso de **VSPerfCmd** como parte de um processo em lote.|  
|[Contador](../profiling/counter.md) **:** `cfg`|Quando o método analisando de exemplo é usado, especifica um contador de CPU e o número de eventos a ser usada como o intervalo de amostragem.  Você pode obter apenas um valor do contador.<br /><br /> Quando a instrumentação que analisa o método é usado, especifica uma CPU ao contrário do seja coletado em cada ponto de gerenciamento.  Use apenas com **Start:**`Trace`, **Attach**,ou **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Exibe uma lista de contadores válidos de CPU do computador atual.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Especifica um evento do contador de desempenho do windows para incluir com dados da marca do perfil.  Use apenas com **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Especifica o intervalo de tempo \(em milissegundos\) entre eventos de coleta de dados do contador de desempenho do windows.  Uso com **WinCounter**.|  
|[Eventos](../profiling/events-vsperfcmd.md) **:** `option`|Controla a coleção de eventos especificados de Rastreamento de Eventos do Windows \(ETW\).  Os dados do ETW são coletados em um arquivo de .itl que não seja o arquivo de dados de perfil .vsp \(\).|  
|[Status](../profiling/status.md)|Exibe o estado do profiler, as informações sobre os processos que estão sendo analisado no momento, e contas que tenham a autoridade para controlar o profiler.|  
|[Desligamento](../profiling/shutdown.md)\[**:**`n`\]|Fecha o arquivo de dados de perfil e desconecta o profiler.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Continua a coleta de dados após uma chamada a **VSPerfCmdGlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Para qualquer coleta de dados, mas não encerra a sessão analisando.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|A coleta de dados de resumos do processo especificado depois de analisar foi pausada por uma chamada a **VSPerfCmdProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Para coleta de dados para o processo especificado.|  
|[ThreadOn e ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Os resumos criação de perfil para o processo especificado depois de analisar foi pausado por uma chamada a **VSPerfCmdThreadOff**.  Use **ThreadOn** apenas ao analisar com o método de gerenciamento.|  
|[ThreadOn e ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Pausa criação de perfil para o thread especificado.  Use **ThreadOff** apenas ao analisar com o método de gerenciamento.|  
|[Marca](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|Insere uma marca no arquivo de dados do perfil, com texto opcional.|  
  
## Opções de método de amostragem  
 As seguintes opções estão disponíveis apenas se você estiver usando a amostragem que analisa o método.  
  
|Opção|Descrição|  
|-----------|---------------|  
|[Iniciar](../profiling/launch.md) **:** *Executable*|Inicia o aplicativo especificado e começar a analisar.|  
|[Args](../profiling/args.md) **:** *Arguments*|Especifica argumentos de linha de comando para passar para o aplicativo iniciado.|  
|[Console](../profiling/console.md)|Inicia o comando especificado em uma nova janela do prompt de comando.|  
|[Anexar](../profiling/attach.md) **:** *PID*\[**,***PID*\]|Inicia a analisar os processos especificados.  Os processos do podem ser identificados pela ID de processo ou pelo nome do processo.|  
|[Desanexar](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|Interrompe aos processos especificados.  Os processos do podem ser identificados pela ID de processo ou pelo nome do processo.  Se nenhum processo for especificado, está analisando paralisado para todos os processos.|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|Coleta a alocação de memória .NET e os dados de tempo de vida do objeto.  Use apenas com a opção de **VSPerfCmdLaunch** .|  
  
### Opções de intervalo de amostragem  
 As seguintes opções especificam o tipo e a duração de intervalos de amostragem.  O padrão é **Timer**.  Você também pode especificar uma CPU exibidos como o intervalo usando a opção de **Counter** .  Essas opções podem ser especificadas somente com **Launch** ou com primeiro **Attach** de uma sessão analisando.  
  
|Opção|Descrição|  
|-----------|---------------|  
|[PF](../profiling/pf.md)\[**:***n*\]|Exemplos em cada falha de página de n \(default\=10\).|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|Exemplos em cada chamada de sistema de n \(default\=10\).|  
|[Temporizador](../profiling/timer.md)\[**:***n*\]|Exemplos em cada ciclo do processador de n \(default\=10000000\).|  
  
## Opções do componente de serviço e de dispositivo do modo kernel  
 As seguintes opções de administração suporte para analisar componentes de serviço ou drivers de dispositivo do modo kernel.  As opções de administração definidas analisando e permissões controlam o serviço ou o driver de dispositivo analisado.  
  
 As opções de administração devem ser executadas em um prompt de comando que está executando com credenciais administrativas.  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|Permite ou nega o acesso especificado de usuário ou grupo para analisar serviços.<br /><br /> `Right` pode ser:<br /><br /> CrossSession \- fornece acesso de usuários ao serviço para fazer analisar cruzado da sessão.<br /><br /> SampleProfiling \- fornece acesso de usuários ao driver para criar perfis amostragem.  Também usado para acessar informações de transição de kernel durante a criação de rastreamento.<br /><br /> FullAccess \- fornece ao usuário acesso de CrossSession e de SampleProfiling.|  
|**Admin:Security, List**|Lista o estado atual de analisar os serviços e lista as permissões de usuário.|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|O iniciar, parar, instalações, ou desinstala o componente de serviço para o serviço \(\) ou o driver de dispositivo do modo kernel \(driver\).|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|Habilita ou desabilita automaticamente iniciar o driver de dispositivo analisando de serviço \(serviço\) ou do modo kernel \(driver\) após o reinício.|  
  
## VSPerfCmd \/Driver  
 A opção de **VSPerfCmd \/Driver** é agora obsoleta.  Use as opções de **VsPerfCmdAdmin** para essa funcionalidade.  
  
## Consulte também  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)