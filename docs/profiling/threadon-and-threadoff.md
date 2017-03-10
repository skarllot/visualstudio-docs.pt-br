---
title: "ThreadOn e ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ThreadOn e ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os VSPerfCmd.exe **ThreadOff** e os subcommands de **ThreadOn** só estão disponíveis na linha de comando que analisa as sessões que usam o método de gerenciamento.  **ThreadOff** e **ThreadOn** pausar e retomar analisar para o thread especificado.  **ThreadOff** para análise do thread e **ThreadOn** inicia analisar o thread.  
  
 Na maioria dos casos, você especifica **ThreadOn** ou **ThreadOff** como a única opção em uma linha de comando de VSPerfCmd.exe, mas também podem ser combinados com **GlobalOn**, **GlobalOff**, **ProcessOn**, e os subcommands de **ProcessOff** .  
  
 Os subcommands de **ThreadOn** e de **ThreadOff** interagem com os subcommands de **GlobalOn** e de **GlobalOff** que controlam a coleta de dados para todos os processos em uma linha de comando que analisa a sessão, e os subcommands de **ProcessOn** e de **ProcessOff** que controlam a coleta de dados para um processo especificado.  
  
 Os subcommands de **ThreadOff** e de **ThreadOn** também afetam a pontuação de thread Iniciar\/parar que é manipulada por funções de API do profiler.  
  
-   define**ThreadOff** imediatamente o thread de início\/contagem de parada a 0 e pausa em virtude disso analisar.  
  
-   define**ThreadOn** imediatamente o thread de início\/contagem de parada a 1 e continua como consequência analisar.  
  
 Para obter mais informações, consulte [APIs de ferramentas de criação de perfil](../profiling/profiling-tools-apis.md).  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### Parâmetros  
 `TID`  
 O identificador do inteiro de thread para iniciar ou parar.  
  
## Opções válidas  
 **ThreadOn** e **ThreadOff** podem ser especificados nas linhas de comando que também contém os seguintes subcommands.  
  
 **Start:** `Method`  
 Inicializa a linha de comando que analisa a sessão e definir o método de perfil especificado.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Interrompe ou inicia a criação de perfil para todos os processos em uma linha de comando que analisa a sessão.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Interrompe ou inicia a criação de perfil para o processo especificado.  
  
## Exemplo  
 Neste exemplo, o subcommand de **ThreadOff** é usado para interromper a coleta de dados de perfil de modo que apenas os dados de inicialização do aplicativo sejam coletados.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)