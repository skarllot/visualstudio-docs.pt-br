---
title: "Depura&#231;&#227;o do ASP.NET: requisitos do sistema | Microsoft Docs"
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
  - "Depurando aplicativos da Web ASP.NET, requisitos do sistema"
  - "Depurando aplicativos da Web ASP.NET, os requisitos de segurança"
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o do ASP.NET: requisitos do sistema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve os requisitos de software e segurança para [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] cenários de depuração:  
  
-   Depuração local no qual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o aplicativo Web em execução no mesmo computador. Há duas versões desse cenário:  
  
    -   O [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] código reside no sistema de arquivos.  
  
    -   O [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] código reside em um site do IIS.  
  
-   Depuração remota, no qual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é executado em um computador cliente e depura um aplicativo Web que está em execução em um computador de servidor remoto.  
  
## Requisitos de segurança  
 Para depuração remota, computadores locais e remotos devem estar em uma configuração de domínio ou uma configuração de grupo de trabalho.  
  
 Para depurar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho, você deve ter permissão para depurar esse processo. Por padrão, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] executar aplicativos como o **ASPNET** usuário. Se o processo de trabalho está sendo executado como **ASPNET**, ou como **NETWORK SERVICE**, você deve ter privilégios de administrador para depurá\-lo.  
  
 O nome do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo varia por cenário de depuração e versão do IIS. Para obter mais informações, consulte [Como localizar o nome do processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Você pode alterar o usuário da conta que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho é executado, editando o arquivo Machine. config no servidor que está executando o IIS. A melhor maneira de fazer isso é usar o **Serviços de informações da Internet \(IIS\) Manager**. Para obter mais informações, consulte [Como executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Se você alterar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho para ser executado em sua própria conta de usuário, você não precisa ser um administrador no servidor que está executando o IIS.  
  
> [!CAUTION]
>  Antes de alterar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho para ser executado em uma conta diferente, considere as possíveis consequências se o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho deve ser invadido ao executar sob essa conta. As contas de usuário ASPNET and NETWORK SERVICE é executado com permissões mínimas, reduzindo o dano possível se o processo for invadido. Se você precisar alterar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho seja executado em uma conta que tenha permissões maiores, o dano potencial é maior.  
  
## Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Como executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md)