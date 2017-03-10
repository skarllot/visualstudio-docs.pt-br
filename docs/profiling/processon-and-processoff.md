---
title: "ProcessOn e ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ProcessOn e ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os VSPerfCmd.exe **ProcessOff** e os subcommands de **ProcessOn** pausar e retomar analisar para o processo especificado em uma linha de comando que analisa a sessão.  **ProcessOff** para análise do processo e analisar **ProcessOn** inicia o processo.  
  
 Na maioria dos casos, você especifica **ProcessOn** ou **ProcessOff** como a única opção em uma linha de comando de VSPerfCmd.exe, mas também podem ser combinados com **GlobalOn**, **GlobalOff**, **ThreadOn**, e os subcommands de **ThreadOff** .  
  
 Os subcommands de **ProcessOn** e de **ProcessOff** interagem com os subcommands de **GlobalOn** e de **GlobalOff** que controlam a coleta de dados para todos os processos em uma linha de comando que analisa a sessão, e os subcommands de **ThreadOn** e de **ThreadOff** que controlam a coleta de dados para um thread especificado.  
  
 Os subcommands de **ProcessOff** e de **ProcessOn** também afetam a pontuação do processo Iniciar\/parar que é manipulada por funções de API do profiler.  
  
-   define**ProcessOff** imediatamente o processo de início\/contagem de parada a 0 e pausa em virtude disso analisar.  
  
-   define**ProcessOn** imediatamente o processo de início\/contagem de parada a 1 e continua como consequência analisar.  
  
 Para obter mais informações, consulte [APIs de ferramentas de criação de perfil](../profiling/profiling-tools-apis.md).  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### Parâmetros  
 `PID`  
 O identificador do inteiro de processo para iniciar ou parar.  As IDs de processo são listados na guia do processo do gerenciador de tarefas do windows.  
  
## Subcommands necessários  
 Nenhum  
  
## Subcommands válidos  
 **ProcessOn** e **ProcessOff** podem ser especificados nas linhas de comando que também contém os seguintes subcommands.  
  
 **Start:** `Method`  
 Inicializa a linha de comando que analisa a sessão e definir o método de perfil especificado.  
  
 **Launch:** `AppName`  
 Inicia o aplicativo especificado e começar a analisar com o método de amostragem.  
  
 **Attach:** `PID`  
 Inicia a analisar o processo especificado.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Interrompe ou inicia a criação de perfil para todos os processos em uma linha de comando que analisa a sessão.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Interrompe ou inicia a criação de perfil para o thread especificado \(método de instrumentação apenas\).  
  
## Exemplo  
 Neste exemplo, o subcommand de **ProcessOff** é usado para coletar dados do perfil para a inicialização do aplicativo.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)