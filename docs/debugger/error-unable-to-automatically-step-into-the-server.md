---
title: "Erro: n&#227;o &#233; poss&#237;vel intervir automaticamente no servidor | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Erro de notificação de depuração, remoto"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: n&#227;o &#233; poss&#237;vel intervir automaticamente no servidor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O erro é:  
  
 Não é possível intervir automaticamente no servidor. O depurador não foi notificado antes do procedimento remoto foi executado  
  
 Esse erro pode ocorrer quando você está tentando entrar em um serviço da web \(consulte [entrar em um serviço Web XML](http://msdn.microsoft.com/pt-br/8e67de38-bf5f-41cc-a457-1b88ce63d764)\). Ele pode ocorrer sempre que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não está configurado corretamente.  
  
 Possíveis causas são:  
  
-   O arquivo Web. config para seu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo não definiu a depuração como "true" \(consulte [modo de depuração em aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)\).  
  
-   Uma versão de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalado depois que o Visual Studio foi instalado.[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] deve ser instalado antes do Visual Studio. Para corrigir esse problema, use o Windows **Painel de controle**, **programas e recursos** reparar sua instalação do Visual Studio.  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)