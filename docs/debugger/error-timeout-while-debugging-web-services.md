---
title: "Erro: tempo limite durante a depura&#231;&#227;o de servi&#231;os Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "depurador, erros de aplicativo Web"
  - "Serviços Web XML, tempo limite durante a depuração"
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: tempo limite durante a depura&#231;&#227;o de servi&#231;os Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você estiver acessando um serviço Web XML do código de chamada, a chamada pode exceder o tempo limite e você não poderá continuar a depuração.  Você pode ver uma mensagem de erro como essa.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## Solução  
 Para evitar esse problema, defina o tempo limite para a chamada ao serviço Web XML como infinito, conforme exibido neste exemplo:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)