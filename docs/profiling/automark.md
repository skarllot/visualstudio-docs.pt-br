---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **AutoMark** especifica o número de milissegundos entre a coleção de eventos do contador de desempenho do software do windows.  Os contadores de desempenho do windows são especificados na opção de **WinCounter** .  
  
 Apenas uma opção de **AutoMark** pode ser especificada na linha de comando.  Observe que o intervalo de amostragem de **WinCounter** especificado por **AutoMark** é independente do intervalo de amostragem principal.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### Parâmetros  
 `Milliseconds`  
 Especifica o número de milissegundos entre coleções de eventos do contador de desempenho do windows.  
  
## Opções necessárias  
 **WinCounter:** `Path`  
 Especifica o que o desempenho ao contrário de coleta.  Quando você estiver usando o método de gerenciamento, vários contadores do windows podem ser especificados.  Quando você usar o método de amostragem, somente um software isso pode ser especificado.  A opção de **WinCounter** deve ser especificada em uma linha de comando que contém a opção de **Start** .  
  
## Exemplo  
 Neste exemplo, um intervalo de amostragem de 1000 milissegundos é definido para dois contadores de desempenho do windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)