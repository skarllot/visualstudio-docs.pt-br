---
title: "Status | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Status
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de VSPerfCmd.exe **Status** exibem informações sobre o estado do profiler e todos os processos que são analisados no momento.  
  
 A opção de **Status** deve ser a única opção especificada na linha de comando.  O profiler deverá ser inicializado com a opção de VSPerfCmd.exe **Start** antes que qualquer status pode ser exibido.  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### Parâmetros  
 Nenhum  
  
## Comentários  
 A opção de **Status** exibe as seguintes informações de estado para o profiler.  
  
 **Output File Name**  
 O caminho e o nome do arquivo de dados atual do profiler.  
  
 **Collection Mode**  
 EXEMPLO ou TRACE  
  
 **Maximum Processes**  
 O número máximo de processos que podem ser analisados ao mesmo tempo e o número de processos ativos atualmente.  
  
 **Maximum Threads**  
 O número máximo de threads que podem ser analisados ao mesmo tempo.  
  
 **Number of Buffers**  
 O número de buffers de memória dedicada a gravar dados de perfil.  
  
 **Size of Buffers**  
 O tamanho em bytes de um buffer de memória.  
  
 A opção de **Status** exibe as seguintes informações de estado de cada processo que está sendo analisado no momento.  
  
 **Process**  
 O nome do processo analisado.  
  
 **Process ID**  
 O identificador de sistema do processo.  
  
 **Num Threads**  
 O número de threads atualmente em execução.  
  
 **Start\/Stop Count**  
 A contagem interna primário do profiler para controlar a coleta de dados para esse processo.  A contagem deve ser igual à coleta de dados.  A contagem de Iniciar\/parar pode ser manipulada pelas APIs do profiler e a opções **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, e **ThreadOff**de VSPerfCmd.  
  
 **Suspend\/Resume Count**  
 A contagem interna secundário do profiler para controlar a coleta de dados para esse processo.  A contagem deve ser menor ou igual a zero para coletar dados.  A contagem de **Suspend\/Resume** pode ser manipulada somente pelas APIs do profiler.  
  
 **Users with access rights to monitor**  
 Lista os nomes de usuários que têm acesso ao profiler.  Os usuários adicionais podem receber acesso usando a opção de VSPerfCmd.exe **Admin**  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)