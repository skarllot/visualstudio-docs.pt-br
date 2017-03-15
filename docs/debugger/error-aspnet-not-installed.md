---
title: "Erro: ASP.NET n&#227;o instalado | Microsoft Docs"
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
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, mensagens de erro de instalação"
  - "depurador, erros de aplicativo Web"
  - "mensagens de erro, ASP.NET"
  - "aplicativos da Web, erros"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: ASP.NET n&#227;o instalado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse erro ocorre quando o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não está instalado corretamente no computador que você está tentando depurar.  Isso pode significar que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nunca foi instalado ou que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalado primeiro e o IIS foi instalado posteriormente.  
  
### Para reinstalar o ASP.NET  
  
1.  De uma janela de prompt de comando, execute o seguinte comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     onde *version* representa o número da versão do .NET Framework instalado no computador, por exemplo, v1.0.370.  Você pode determinar a versão do framework examinando o diretório `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    >  Com o Windows Server 2003, você pode instalar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando **Adicionar ou Remover Programas** no Painel de Controle.  
  
## Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)