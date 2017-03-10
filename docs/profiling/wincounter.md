---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **WinCounter** especifica o windows ou o desempenho do aplicativo ao contrário de coleta em intervalos definidos durante a execução do perfil.  O windows e os contadores de desempenho do aplicativo são listados como as marcas nos dados de perfil arquivo.  Você pode especificar vários contadores de desempenho para coletar nas opções separadas.  
  
 Por padrão, os contadores são coletados cada 500 milissegundos.  Use a opção de **AutoMark** especificar um intervalo diferente da coleção.  
  
 Apenas uma opção de **AutoMark** é usada.  Se várias opções de **AutoMark** forem especificadas, a última será usado.  
  
 A opção de **WinCounter** pode ser usada apenas com a opção de **Start** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### Parâmetros  
 `Path`  
 O desempenho do windows contrário do formato do caminho do contador de PDH.  
  
## Opções necessárias  
 A opção de **WinCounter** pode ser usada apenas com a opção de **Start** .  
  
 **Start:** `Method`  
 A opção de **Start** inicializa o profiler para o método de perfil especificado.  
  
## Opções exclusivas  
 A opção de **AutoMark** pode ser usada apenas com a opção de **WinCounter** .  
  
 **AutoMark:** `Milliseconds`  
 Especifica o número de milissegundos entre a coleta de dados do contador de desempenho do windows.  
  
## Exemplo  
 No exemplo a seguir, dois contadores de desempenho do windows são especificados para ser coletados em um intervalo de 1000 milissegundos.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)