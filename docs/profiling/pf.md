---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As opções definidas de VSPerfCmd.exe **PF** o evento analisando que é uma amostra feita a falhas de página, e alterar o número de falhas de página em um intervalo de amostragem padrão de 10.  
  
> [!NOTE]
>  O PF não pode ser usado em sistemas de 64 bits.  
  
 **Observação**  
 **PF** não tem suporte em computadores de 64 bits.**PF** só pode ser usado em uma linha de comando que também contém **Launch** ou a opção de **Attach** .  
  
 Por padrão, o evento de amostragem será definida com os ciclos de formato não paralisados de processador e o intervalo de amostragem será definido como 10.000.000.  **Timer**, **PF**, **Sys**, e as opções de **Counter** permite definir o intervalo de exemplo do evento e de amostragem.  A opção de **GC** coleta dados de memória .NET em cada evento de alocação e coleta de lixo.  Apenas uma dessas opções pode ser especificado em uma linha de comando.  
  
 O intervalo de evento amostragem e de amostragem pode ser definido apenas na primeira linha de comando que contém **Launch** ou uma opção de **Attach** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### Parâmetros  
 `Events`  
 Um valor inteiro que especifica o número de eventos de falha de página em um intervalo de amostragem.  Se `Events` não for especificado, o intervalo é definido como 10.  
  
## Opções necessárias  
 **PF** só pode ser especificado em uma linha de comando que contém uma das opções a seguir.  
  
 **Launch:** `AppName`  
 Inicia o profiler e o aplicativo especificados por AppName.  
  
 **Attach:** `PID`  
 Anexa o profiler para o processo especificado por AppName.  
  
## Opções inválidas  
 As opções a seguir não podem ser especificadas na mesma linha de comando que **PF**.  
  
 **Timer**\[**:**`Cycles`\]  
 Define o evento de amostragem aos ciclos do relógio do processador e define o intervalo de amostragem a `Cycles`.  O intervalo padrão de timer é 10.000.000.  
  
 **Sys**\[**:**`Events`\]  
 Define o evento de amostragem ao aplicativo chama analisado ao kernel do sistema operacional \(syscalls\) e define o intervalo de amostragem a `Events`.  O intervalo do sistema de opção é 10.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Define o evento de amostragem ao contador de desempenho de CPU especificado por `Name` e define o intervalo de amostragem a `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Coleta dados de memória do .NET.  Por**Allocation**\(padrão\), os dados são coletados em cada evento de alocação de memória.  Quando o parâmetro de **Lifetime** for especificado, os dados são coletados também em cada evento de coleta de lixo.  
  
## Exemplo  
 Este exemplo demonstra como definir o evento de exemplo analisando a falhas de página e definir o intervalo de amostragem a 20 falhas de página.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)