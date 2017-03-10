---
title: "Desligamento | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Desligamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **Shutdown** espera qualquer processo em analisado para terminar ou desanexar, e depois desconecta o profiler e fecha o arquivo de dados de perfil.  A opção de **Shutdown** deve ser o último comando de analisar executado.  
  
 Se um parâmetro de tempo limite não for especificado, a opção de **Shutdown** aguardará indefinidamente.  Se um parâmetro de tempo limite é especificado, a opção retorna depois que o número de segundos especificado sem desligar o profiler ou feche o arquivo de dados.  
  
 A opção de **Shutdown** deve ser a única opção especificada na linha de comando.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### Parâmetros  
 `Timeout`  
 -   \(Opcional\) Se for especificada, a opção retorna depois que o número de segundos especificado sem desligar o profiler ou feche os dados de perfil arquivos.  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)