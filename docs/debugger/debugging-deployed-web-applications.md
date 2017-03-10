---
title: "Depurando aplicativos Web implantados | Microsoft Docs"
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
  - "Aplicativos Web ASP.NET"
  - "ASP.NET, depurando aplicativos da Web"
  - "depurando serviços Web"
  - "Serviços Web, depuração"
  - "Serviços Web XML, depuração"
  - "XML, depurando serviços Web"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando aplicativos Web implantados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você precisar depurar um aplicativo Web que está sendo executado em um servidor de produção, isso deverá ser feito com cuidado.  Se você anexar ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para depurar e atingir um ponto de interrupção, por exemplo, todo o código gerenciado no processo de trabalho é interrompido.  Interromper todo o código gerenciado no processo de trabalho pode causar uma parada de trabalho para todos os usuários no servidor.  Antes de depurar em um servidor de produção, considere o impacto potencial no trabalho de produção.  
  
 Para usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para depurar um aplicativo implantado, você deverá anexar ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e verificar se o depurador tem acesso aos símbolos para o aplicativo.  Você também deve localizar e abrir os arquivos de origem para o aplicativo.  Para obter mais informações, consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Como localizar o nome do processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) e [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Muitos aplicativos Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fazem referência às DLLs que contêm a lógica de negócios ou outro código útil.  Essa referência copia automaticamente a DLL do computador local para a pasta \\bin do diretório virtual do aplicativo Web.  Quando você estiver depurando, lembre\-se de que o aplicativo Web está referenciando essa cópia da DLL e não a cópia em seu computador local.  
  
 O processo para anexar ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é o mesmo que anexar a qualquer outro processo remoto.  Quando você está anexado, se não tiver o projeto correto aberto, uma caixa de diálogo aparecerá quando o aplicativo for interrompido.  Essa caixa de diálogo solicita o local dos arquivos de origem para o aplicativo.  O nome do arquivo que você especifica na caixa de diálogo deve corresponder ao nome de arquivo especificado nos símbolos de depuração no servidor Web.  Para obter mais informações, consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Depurando aplicativos Web e script](../debugger/debugging-web-applications-and-script.md)   
 [Como habilitar a depuração para aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Como localizar o nome do processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)