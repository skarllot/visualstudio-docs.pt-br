---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **GC** habilita a coleção de alocação de memória do .NET Framework e os dados de tempo de vida do objeto.  A opção de **GC** pode ser usada apenas com a amostragem que analisa o método e apenas com a opção de **Launch** .  
  
 Quando você estiver usando a opção de **GC** , o comando de VSPerfClrEnv **\/sampleon** não é necessário.  
  
 Se nenhum parâmetro for especificado, ou se o parâmetro de **Allocation** for especificado, somente os dados de alocação de memória do .NET Framework são coletados.  Se o parâmetro de **Lifetime** for especificado, a alocação de memória do.NET Framework e os dados de tempo de vida do objeto do .NET Framework são coletados.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### Parâmetros  
 **Allocation**  
 Padrão.  Coleta dados de alocação de memória do.NET Framework.  
  
 **Lifetime**  
 Coleta dados de alocação de memória do.NET Framework e dados de tempo de vida do objeto do.NET Framework.  
  
## Opções necessárias  
 A opção de **GC** pode ser usada apenas com a opção de **Launch** .  
  
 **Launch:** `AppName`  
 Inicia o aplicativo especificado e começar a analisar com o método de amostragem.  
  
## Exemplo  
 O exemplo a seguir inicia um aplicativo e coletar dados de alocação de memória do.NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)