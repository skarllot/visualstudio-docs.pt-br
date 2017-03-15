---
title: "Como usar Editar e Continuar (C#) | Microsoft Docs"
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
  - "Editar e Continuar [C#], sobre Editar e Continuar"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar Editar e Continuar (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Com a função Editar e Continuar no C\#, é possível fazer alterações em seu código no modo de interrupção durante a depuração.  As alterações podem ser aplicadas sem precisar interromper e reiniciar a sessão de depuração.  
  
 A função Editar e Continuar é automaticamente invocada quando você faz alterações no modo de interrupção e, em seguida, escolhe um comando de execução no depurador, como **Continuar**, **Etapa** ou **Definir próxima instrução** ou avalia uma função em uma janela de depuração.  
  
> [!NOTE]
>  A função Editar e Continuar não tem suporte ao depurar o Compact Framework, código otimizado, código nativo misto\/gerenciado ou código de integração do SQL Server Common Language Runtime \(CLR\).  Se você tentar aplicar alterações de código em um desses cenários, o depurador coloca uma caixa de diálogo explicando que a função Editar e Continuar não tem suporte.  
  
### Para invocar a função Editar e Continuar automaticamente  
  
1.  No modo de interrupção, faça uma alteração no código\-fonte.  
  
2.  No menu **Depurar**, clique em **Continuar**, **Etapa** ou **Definir próxima instrução** ou avalie uma função em uma janela de depuração.  
  
     O novo código é compilado e a depuração continua com o novo código.  Algumas alterações não têm suporte para a função Editar e Continuar.  Para obter mais informações, consulte [Alterações de código suportadas \(C\#\)](../debugger/supported-code-changes-csharp.md).  
  
### Para habilitar\/desabilitar a função Editar e Continuar  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Na caixa de diálogo **Opções**, expanda o nó **Depuração** e selecione **Editar e Continuar**.  
  
3.  Na caixa de diálogo **Opções** da página **Editar e Continuar**, marque ou desmarque a caixa de seleção **Habilitar Editar e Continuar**.  
  
     A configuração entra em vigor quando você reinicia a sessão de depuração.  
  
## Consulte também  
 [Editar e continuar \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Alterações de código suportadas \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [Erros e avisos de Editar e Continuar \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)