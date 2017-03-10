---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Por padrão, o profiler coleta número da linha de origem e a linha de dados do deslocamento de números quando você estiver usando a amostragem que analisa o método.  A opção de VSPerfCmd **LineOff** desabilita a linha coleta de dados de número VSPerfCmd quando é usado para iniciar o aplicativo.  Os dados de perfil são coletados para o nível da função quando **LineOff** é especificado.  
  
 Você pode usar **LineOff** somente com a opção de **Launch** , e apenas quando o profiler for inicializado para criar uma amostra de **Start**usando: opção de**Sample** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### Parâmetros  
 Nenhum  
  
## Opções necessárias  
 A opção de **LineOff** só pode ser usada em uma linha de comando que contém a opção de **Launch** .  
  
 **Launch:** `AppName`  
 Inicia o aplicativo especificado e começar a analisar com o método de amostragem.  
  
## Exemplo  
 Esse exemplo inicia o aplicativo e o profiler, e desabilita a amostragem de linha de nível.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)