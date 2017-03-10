---
title: "Usu&#225;rio (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usu&#225;rio (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **User** especifica o domínio e o nome de usuário da conta que possui o processo analisado.  Essa opção é necessária somente se o processo estiver sendo executado como um usuário diferente do usuário conectado.  O proprietário do processo é listado na coluna de nome de usuário na guia de processos do gerenciador de tarefas do Windows.  
  
 A opção de **User** só pode ser especificada em uma linha de comando que também contém a opção padrão de **Start** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### Parâmetros  
 `Domain`  
 O nome do domínio do usuário.  
  
 `UserName`  
 O nome do usuário.  
  
## Opções necessárias  
 A opção de **User** pode ser usada apenas com a opção de **Start** .  
  
 **Start:** `Method`  
 Inicializa o profiler para o método de perfil especificado.  
  
## Exemplo  
 O exemplo a seguir demonstra o uso da opção de **User** .  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)