---
title: "Otimiza&#231;&#227;o e depura&#231;&#227;o JIT | Microsoft Docs"
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
  - "depurando [Visual Studio], código otimizado"
  - "código otimizado, depuração"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Otimiza&#231;&#227;o e depura&#231;&#227;o JIT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você depura um aplicativo gerenciado, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] suprime a otimização de código Just\-In\-Time \(JIT\) por padrão.  A supressão da otimização JIT significa que você está depurando código não otimizado.  O código é executado um pouco mais lentamente porque não é otimizado, mas sua experiência de depuração é muito mais completa.  A depuração de código otimizado é mais difícil e recomendada somente se você encontrar um bug no código otimizado que não pode ser reproduzido na versão não otimizada.  
  
 A otimização JIT é controlada no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pela opção **Suprimir otimização JIT no carregamento do módulo**.  Você pode encontrar essa opção na página **Geral** sob o nó **Depuração** na caixa de diálogo **Opções**.  
  
 Se você desmarcar a opção **Suprimir otimização JIT no carregamento do módulo**, poderá depurar o código JIT otimizado, mas sua capacidade de depuração poderá ser limitada porque o código otimizado não corresponde ao código\-fonte.  Como resultado, as janelas de depuração como as janelas **Locais** e **Autos** podem não exibir tanta informação quanto exibiriam se você estivesse depurando código não otimizado.  
  
 Outra diferença importante está relacionada à depuração com Apenas Meu Código.  Se você estiver depurando com Apenas Meu Código, o depurador considerará o código otimizado como código de não usuário, que não deve ser exibido durante a depuração.  Consequentemente, se estiver depurando código otimizado JIT, provavelmente será conveniente desativar Apenas Meu Código.  Para obter mais informações, consulte [Restringir a depuração a Apenas Meu Código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Lembre\-se de que a opção **Suprimir otimização JIT no carregamento do módulo** suprime a otimização de código quando os módulos são carregados.  Se você anexar a um processo que já estiver em execução, ele poderá conter código já carregado, compilado por JIT e otimizado.  A opção **Suprimir otimização JIT no carregamento do módulo** não tem efeito nesse código, embora afete os módulos que são carregados depois da anexação.  Além disso, a opção **Suprimir otimização JIT no carregamento do módulo** não afeta módulos, como WinForms.dll, criados com NGEN.  
  
## Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo de execução gerenciada](../Topic/Managed%20Execution%20Process.md)