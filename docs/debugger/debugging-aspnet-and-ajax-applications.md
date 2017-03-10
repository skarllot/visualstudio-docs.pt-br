---
title: "Depurando aplicativos ASP.NET e AJAX | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuração [ASP.NET], sobre depuração do ASP.NET"
  - "depurando aplicativos Web ASP.NET"
  - "depuração, WCF"
  - "WCF, depuração"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando aplicativos ASP.NET e AJAX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Depurar aplicativos Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é semelhante a depurar o Windows Form ou qualquer outro aplicativo do Windows porque ambos os tipos de aplicativos envolvem controles e eventos.  No entanto, também há diferenças básicas entre os dois tipos de aplicativos:  
  
-   Controlar o estado é mais complexo em um aplicativo Web.  
  
-   Em um aplicativo do Windows, o código a ser depurado está na maioria das vezes em um local; em um aplicativo Web, o código pode estar no cliente e no servidor.  Embora o código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] esteja todo no servidor, pode haver também código JavaScript ou código do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no cliente.  
  
## Nesta seção  
 [Preparando\-se para depurar ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Descreve as etapas necessárias para habilitar a depuração de aplicativos do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Depurando aplicativos Web](../debugger/debugging-web-applications.md)  
 Discute como depurar um aplicativo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], incluindo aplicativos de script habilitados para AJAX.  
  
## Seções relacionadas  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)  
 Explica por que apenas Just My Code deve ser habilitado para depurar exceções do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 Discute algumas técnicas e ferramentas que podem ajudar a depurar seu código AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Depure seu código mais rápido com IntelliTrace para registrar e examinar um histórico do estado do aplicativo sem reiniciar o aplicativo com tanta frequência.  Você pode ver informações sobre os eventos e as chamadas que ocorrem durante a execução do aplicativo e começar a depuração a partir desses pontos no tempo.  Exige o Visual Studio Ultimate.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando aplicativos Web e script](../debugger/debugging-web-applications-and-script.md)   
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)