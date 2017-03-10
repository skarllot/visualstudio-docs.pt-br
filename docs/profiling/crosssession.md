---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de VSPerfCmd.exe **CrossSession** habilita o profiler para coletar dados de qualquer sessão do console.  A opção de **CrossSession** deve ser usada com a opção de **Start** .  
  
 Você pode usar a abreviação **CS** em vez disso **CrossSession**.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### Parâmetros  
 Nenhum  
  
## Opções válidas  
 Para criar perfis em outra sessão, a opção de **CrossSession** deve ser especificada com a opção de **Start** .  **CrossSession** também deve ser especificado em qualquer **VSPerfCmd Attach** e comandos subsequentes de **Detach** .  
  
 **Start:** `Method`  
 A opção de **Start** inicializa o profiler para o método de perfil especificado.  
  
 **Attach:** *PID*\[**,***PID*\]  
 Inicia a analisar os processos especificados.  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 Interrompe aos processos especificados.  
  
## Exemplo  
 Neste exemplo, a opção de **CrossSession** é usada para anexar um aplicativo que é iniciado em outra sessão do console.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)