---
title: "Pr&#233;-requisitos para aplicativos Web de depura&#231;&#227;o remota | Microsoft Docs"
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
  - "depurando aplicativos Web ASP.NET, servidores remotos"
  - "depuração remota, pré-requisitos"
  - "servidores remotos, depurando aplicativos da Web"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pr&#233;-requisitos para aplicativos Web de depura&#231;&#227;o remota
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Com o depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode depurar um aplicativo Web de maneira transparente no computador local ou em um servidor remoto.  Isso significa que o depurador funciona da mesma maneira e permite que você use os mesmos recursos em qualquer computador.  Para que a depuração remota funcione corretamente, no entanto, há alguns pré\-requisitos.  
  
-   Os componentes da depuração remota do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] devem estar instalados no servidor que você deseja depurar.  Para obter mais informações, consulte [Configuração de depuração remota](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
-   Por padrão, o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é executado como um processo de usuário do ASPNET.  Como resultado, você deve ter privilégios de Administrador no computador no qual o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é executado para depurá\-lo.  O nome do processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varia de acordo com o cenário de depuração e a versão do IIS.  Para obter mais informações, consulte [Como localizar o nome do processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)