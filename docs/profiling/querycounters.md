---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As listas de opção de **QueryCounters** os contadores de desempenho de CPU \(hardware\) que estão disponíveis no computador.  
  
 **QueryCounters** deve ser a única opção na linha de comando.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### Parâmetros  
 Nenhum  
  
## Comentários  
 Quando você estiver usando o método de gerenciamento, o profiler pode coletar os valores de um ou mais contadores de desempenho de CPU em cada evento de coleta de dados.  Quando você estiver usando a amostragem que analisa o método, você pode especificar um evento vez e o número de ocorrências do evento a ser usadas como o intervalo de amostragem.  
  
 Os processadores diferentes expõe diferentes contadores de desempenho de CPU.  O profiler define um conjunto de contadores genéricas que podem ser usados em quase todos os processadores.  As listas de opção de **QueryCounters** os nomes dos contadores genéricas e os nomes dos contadores que são específicos do processador.  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)