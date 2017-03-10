---
title: "Temporizador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Temporizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção VSPerfCmd.exe **Timer** define o evento de criação de perfil com amostragem para ciclos de relógio do processador e pode alterar o número de ciclos em um intervalo de amostragem do padrão de 10.000.000.  Em um processador de 1 GHz \(um gigahertz\), 10.000.000 ciclos de relógio são aproximadamente 100 amostras por segundo.  O número mínimo de ciclos que pode ser especificado é 50.000.  
  
 **Timer** só pode ser usado quando você utiliza o método de criação de perfil de amostragem e só pode ser usado em uma linha de comando que também contenha a opção **Launch** ou **Attach**.  
  
 Por padrão, o evento de amostragem do criador de perfil é definido como ciclos de relógio do processador e o intervalo de amostragem é definido como 10.000.000.  As opções **Timer**, **PF**, **Sys** e **Counter** permitem definir o evento de amostragem e o intervalo de amostragem.  A opção **GC** coleta dados da memória do .NET em cada alocação e o evento da coleta de lixo.  Apenas uma dessas opções pode ser especificada em uma linha de comando.  
  
 O evento de amostragem e o intervalo de amostragem só podem ser definidos na primeira linha de comando que contém uma opção **Launch** ou **Attach**.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### Parâmetros  
 `Cycles`  
 Um valor inteiro que especifica o número de ciclos de relógio do processador em um intervalo de amostragem.  Caso `Cycles` não seja especificado, o intervalo é definido como 10.000.000.  Especifique o valor sem vírgulas.  
  
## Opções obrigatórias  
 **Timer** só pode ser especificado em uma linha de comando que contenha uma das opções a seguir.  
  
 **Launch:** `AppName`  
 Inicia o criador de perfil e o aplicativo especificado por `AppName`.  
  
 **Attach:** `PID`  
 Anexa o criador de perfil ao processo especificado pela ID de processo \(`PID`\).  
  
## Opções inválidas  
 As opções a seguir não podem ser especificadas na mesma linha de comando de **Timer**.  
  
 **PF**\[**:**`Events`\]  
 Define o evento de amostragem como falhas de página e, como opção, define o intervalo de amostragem como `Events`.  O intervalo de PF padrão é 10.  
  
 **Sys**\[**:**`Events`\]  
 Define o evento de amostragem como chamadas do sistema operacional e, como opção, define o intervalo de amostragem como `Events`.  O intervalo de Sys padrão é 10.  
  
 **Counter**\[**:**`Name,Reload,FriendlyName`\]  
 Define o evento de amostragem como contador de desempenho da CPU especificado por `Name` e define o intervalo de amostragem como `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Coleta dados da memória do .NET.  Por padrão \(**Allocation**\), os dados são coletados em todos os eventos de alocação da memória.  Quando o parâmetro **Lifetime** é especificado, os dados também são coletados em todos os eventos de coleta de lixo.  
  
## Exemplo  
 Esse exemplo demonstra como definir o intervalo de amostragem da criação de perfil como 1.000.000 ciclos de processador.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)