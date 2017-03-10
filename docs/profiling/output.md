---
title: "Sa&#237;da | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sa&#237;da
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A opção de **Output** especifica o nome do arquivo de dados do perfil para a sessão de desempenho.  **Output** deve ser usado com a opção de **Start** .  
  
## Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parâmetros  
 `FileName`  
 O nome do arquivo de dados.  Caminhos completos e parciais são aceitos.  Se um caminho não for especificado, o arquivo é criado no diretório atual.  
  
## Opções necessárias  
 A opção de **Output** deve ser usada com a opção de **Start** .  
  
 **Start:** `Method`  
 Especifica o nome do arquivo de saída.  
  
## Exemplo  
 No exemplo a seguir, o arquivo de dados de perfil é criado no diretório atual.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web do ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)