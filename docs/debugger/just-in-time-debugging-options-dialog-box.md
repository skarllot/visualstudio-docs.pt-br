---
title: "Caixa de di&#225;logo Just-In-Time, Depura&#231;&#227;o, Op&#231;&#245;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Debugger.JIT"
  - "vs.debug.options.JIT"
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
  - "Depuração Just-In-Time, definindo opções"
  - "caixa de diálogo Opções, depuração"
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Just-In-Time, Depura&#231;&#227;o, Op&#231;&#245;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para acessar a página **Just\-In\-Time**, vá até o menu **Ferramentas** e clique em **Opções**.  Na caixa de diálogo **Opções**, expanda o nó **Depuração** e selecione **Just\-In\-Time**.  Essa página permite habilitar a depuração Just\-In\-Time para o código gerenciado, o código nativo e o script.  Para obter mais informações, consulte [Depuração Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Você pode habilitar a depuração Just\-In\-Time para estes tipos de programa:  
  
-   Gerenciado  
  
-   Nativo  
  
-   Script  
  
 A depuração Just\-In\-Time é uma técnica para depurar um programa que é iniciado fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Você pode executar um programa criado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fora do ambiente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se você tiver habilitado a depuração Just\-In\-Time, uma falha exibirá uma caixa de diálogo que perguntará se você quer depurar.  
  
## Avisos associados  
 Quando você visita esta página da caixa de diálogo **Opções**, poderá ver uma mensagem de aviso assim:  
  
 **Outro depurador se registrou como depurador Just\-In\-Time.  Para reparar, habilite a depuração Just\-In\-Time ou execute o reparo do Visual Studio.**  
  
 Essa mensagem ocorrerá se você tiver outro depurador, possivelmente uma versão anterior do depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definida como o depurador Just\-In\-Time.  
  
 Outra mensagem que você pode ver é o seguinte:  
  
 **Erros do registro de depuração Just\-In\-Time detectados.  Para reparar, habilite a depuração Just\-In\-Time ou execute o reparo do Visual Studio.**  
  
 Se você vir qualquer um desses avisos, a depuração Just\-In\-Time com o [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] exigirá privilégios de administrador até você poder solucionar o problema.  Se você tentar habilitar como um não administrador nessas condições, verá a seguinte mensagem de erro:  
  
 **O acesso foi negado.  Faça um administrador habilitar a depuração Just\-In\-Time ou reparar a instalação do Visual Studio.**  
  
## Consulte também  
 [Caixa de diálogo Depuração, Opções](../debugger/debugging-options-dialog-box.md)   
 [Como especificar configurações do depurador](../debugger/how-to-specify-debugger-settings.md)