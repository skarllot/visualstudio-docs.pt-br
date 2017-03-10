---
title: "Como depurar aplicativos Web | Microsoft Docs"
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
  - "Web Forms do ASP.NET, depuração"
  - "ASP.NET, depurando aplicativos da Web"
  - "depurando aplicativos Web ASP.NET, durante o desenvolvimento"
  - "Serviços Web, depuração"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar aplicativos Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é a tecnologia primária para desenvolver aplicativos Web no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  O depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece ferramentas avançadas para depurar aplicativos Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] localmente ou em um servidor remoto.  Este tópico descreve como depurar um projeto do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] durante o desenvolvimento.  Para obter informações sobre como depurar um aplicativo Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] já implantado em um servidor de produção, consulte [Depurando aplicativos Web implantados](../debugger/debugging-deployed-web-applications.md).  
  
 Para depurar um aplicativo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
-   Você deve ter as permissões necessárias.  Para obter mais informações, consulte [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
-   A depuração do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] deve ser habilitada em **Propriedades do Projeto**.  
  
-   O arquivo de configuração do aplicativo \(Web.config\) deve ser definido para o modo de depuração.  O modo de depuração faz com que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] gere símbolos para arquivos gerados dinamicamente e permite que o depurador se anexe ao aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] define isso automaticamente quando você inicia a depuração, caso você tenha criado o projeto do modelo Projetos Web.  
  
-   Para obter mais informações, consulte [Como habilitar a depuração para aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### Para depurar um aplicativo Web durante o desenvolvimento  
  
1.  No menu **Depurar**, clique em **Iniciar** para iniciar a depuração do aplicativo Web.  
  
     O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria o projeto de aplicativo Web, implanta o aplicativo se for necessário, inicia o ASP.NET Development Server se você estiver depurando localmente e anexa ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Use o depurador para definir e desmarcar pontos de interrupção, depurar e executar outras operações de depuração, como faria para qualquer aplicativo.  
  
     Para obter mais informações, consulte [Noções básicas do depurador](../debugger/debugger-basics.md).  
  
3.  No menu **Depurar**, clique em **Parar Depuração** para terminar a sessão de depuração ou, no menu **Arquivo** no Internet Explorer, clique em **Fechar**.  
  
## Consulte também  
 [Depurando aplicativos Web e script](../debugger/debugging-web-applications-and-script.md)   
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Como habilitar a depuração para aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)