---
title: "Como intervir em servi&#231;os WCF | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "depuração, WCF"
  - "WCF, depuração"
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como intervir em servi&#231;os WCF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], você pode entrar em um serviço WCF.  Se o serviço WCF estiver na mesma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que o cliente, você poderá usar pontos de interrupção no serviço WCF.  
  
 Para que a depuração funcione, você deve ter a depuração habilitada no arquivo app.config ou Web.config.  Para obter informações sobre como habilitar a depuração e para obter as limitações para entrar nos serviços WCF, consulte [Limitações da depuração WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Para entrar em um serviço WCF  
  
1.  Crie uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contém os projetos de cliente WCF e serviço WCF.  
  
2.  No Gerenciador de Soluções, clique com o botão direito do mouse no projeto Cliente WCF e clique em **Definir como projeto de inicialização**.  
  
3.  Habilite a depuração no arquivo app.config ou web.config.  Para obter mais informações, consulte [Limitações da depuração WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Defina um ponto de interrupção no local no projeto de cliente onde você deseja iniciar a entrada.  Normalmente, isso será imediatamente antes da chamada de WCF.  
  
5.  Execute o ponto de interrupção e inicie a entrada.  O depurador entrará no serviço automaticamente.  
  
## Consulte também  
 [Depurando serviços WCF](../debugger/debugging-wcf-services.md)   
 [Limitações da depuração WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Como depurar um serviço WCF auto\-hospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md)