---
title: "Desanexar | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Desanexar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Opção de VSPerfCmd.exe **Detach** desconectam o profiler de processos especificado ou todos os processos se nenhum é especificada.  Analisar deve ter sido inicializada usando o método de amostragem.  
  
 Analisando que foi iniciado com ou **Launch** ou as opções de **Attach** podem ser desconectada com **Detach**.  O profiler pode ser reattched usando comandos subsequentes de **Attach** .  
  
 **Detach** não fecha o arquivo de dados de perfil.  Use a opção de **Shutdown** terminar analisar e feche o arquivo de dados.  
  
> [!NOTE]
>  Se a opção de **Start** foi especificada com a opção de **Crosssession** , todas as chamadas a **VSPerfCmd \/Attach** ou a **VSPerfCmd \/Detach** deve também especificar **Crosssession**.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### Parâmetros  
 `PIDs|ProcessNames`  
 `PID` \- o identificador numérico do sistema de um ou vários processos.  
  
 `ProcessNames` \- o nome do processo.  Se várias instâncias do processo chamado está sendo executado, os resultados serão imprevisíveis.  
  
 Processos separados de vários com vírgulas.  
  
 Se nenhum processo for especificado, o profiler for desanexado de qualquer processo analisado.  
  
## Opções válidas  
 As seguintes opções de **VSPerfCmd** podem ser combinadas com a opção de **Attach** em uma única linha de comando.  
  
 **Crosssession**  
 Permite analisar aplicativos nas sessões diferentes da sessão de logon.  Obrigatório se a opção de **Start** foi especificada com a opção de **Crosssession** .  
  
## Exemplo  
 Neste exemplo, o comando de suspender **Detach** analisar e o comando de **Shutdown** fecha o arquivo de dados do profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)