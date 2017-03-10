---
title: "Console | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de VSPerfCmd.exe **Console** inicia o aplicativo especificado em uma nova janela do prompt de comando.  **Console** só pode ser usado com a opção de VSPerfCmd **Launch** .  Se o aplicativo não é um aplicativo de linha de comando, **Console** não tem nenhum efeito.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### Parâmetros  
 Nenhum  
  
## Opções necessárias  
 **Console** só pode ser especificado em uma linha de comando que também contém a opção de **Launch** .  
  
 **Launch:** `AppName`  
 Inicia o profiler e o aplicativo especificados por `AppName`.  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)