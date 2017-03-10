---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As opções definidas de VSPerfCmd.exe **Sys** o evento analisando que é uma amostra feita nos eventos de chamada do sistema \(chamadas de função de aplicativo analisado para o sistema operacional\), e alterar o número de chamadas do sistema em um intervalo de amostragem padrão de 10.  
  
 **Sys** só pode ser usado em uma linha de comando que também contém **Launch** ou a opção de **Attach** .  
  
 Por padrão, o evento de amostragem do profiler for definida com os ciclos do relógio do processador e o intervalo de amostragem será definido como 10.000.000.  **Timer**, **PF**, **Sys**, e as opções de **Counter** permite definir o evento de amostragem e o intervalo de amostragem.  A opção de **GC** coleta dados de memória .NET em cada evento de alocação e coleta de lixo.  Apenas uma dessas opções pode ser especificado em uma linha de comando.  
  
 O evento amostragem e o intervalo de amostragem podem ser definidos apenas na primeira linha de comando que contém **Launch** ou uma opção de **Attach** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### Parâmetros  
 `Events`  
 Um valor inteiro que especifica o número de eventos de chamada do sistema em um intervalo de amostragem.  Se `Events` não for especificado, o intervalo é definido como 10.  
  
## Opções necessárias  
 **Sys** exige uma das opções a seguir.  
  
 **Launch:** `AppName`  
 Inicia o profiler e o aplicativo especificados por `AppName`.  
  
 **Attach:** `PID`  
 Anexa o profiler para o processo especificado por `PID`.  
  
## Opções inválidas  
 As opções a seguir não podem ser especificadas na mesma linha de comando que **Sys**.  
  
 **PF**\[**:**`Events`\]  
 Define o evento de amostragem a falhas de página e define o intervalo de amostragem a `Events`.  O intervalo de PF de opção é 10.  
  
 **Timer**\[**:**`Cycles`\]  
 Define o evento de amostragem aos ciclos do relógio do processador e define o intervalo de amostragem a `Cycles`.  O intervalo padrão de timer é 10.000.000.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Define o evento de amostragem ao contador de desempenho de CPU especificado por `Name` e define o intervalo de amostragem a `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Coleta dados de memória do .NET.  Por**Allocation**\(padrão\), os dados são coletados em cada evento de alocação de memória.  Quando o parâmetro de **Lifetime** for especificado, os dados são coletados também em cada evento de coleta de lixo.  
  
## Exemplo  
 Este exemplo demonstra como definir o evento de amostragem do profiler para chamadas do sistema e como definir o intervalo de amostragem a 20 chamadas pelo exemplo.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)