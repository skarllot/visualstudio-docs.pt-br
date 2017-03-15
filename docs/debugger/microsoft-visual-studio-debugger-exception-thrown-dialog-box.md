---
title: "Caixa de di&#225;logo Depurador do Microsoft Visual Studio (Exce&#231;&#227;o Lan&#231;ada) | Microsoft Docs"
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
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, exceções"
  - "tratamento de exceção, durante a depuração"
  - "Caixa de diálogo do Depurador do Microsoft Visual Studio (Exceção Lançada)"
  - "lançando exceções, durante a depuração"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Depurador do Microsoft Visual Studio (Exce&#231;&#227;o Lan&#231;ada)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ocorreu uma exceção no seu programa.  Esta caixa de diálogo relata o tipo de exceção lançada.  Seu código precisa tratar essa exceção.  Você pode escolher entre as seguintes opções para tratar a exceção:  
  
 **Interromper**  
 Permite que a execução seja interrompida no depurador.  O manipulador de exceção não será invocado antes da interrupção.  Se você continuar a partir da interrupção, o manipulador de exceção será invocado.  
  
 **Continuar**  
 Permite que a execução continue, dando ao manipulador de exceção a possibilidade de tratar a exceção.  Essa opção não está disponível para determinados tipos de exceções.  **Continuar** permite que o aplicativo continue.  Em um aplicativo nativo, ela fará com que a exceção seja relançada.  Em um aplicativo gerenciado, ela fará com que o programa seja encerrado ou a exceção seja tratada por um aplicativo de hospedagem.  
  
> [!NOTE]
>  Você não pode continuar depois de uma exceção sem tratamento em código gerenciado.  A escolha de **Continuar** depois de uma exceção sem tratamento em código gerenciado faz com que a depuração pare.  
  
 **Ignorar**  
 Permite que a execução continue sem invocar o manipulador de exceção.  Como o manipulador de exceção não é invocado, isso poderá resultar em outras consequências, incluindo erros e exceções adicionais.  Essa opção não está disponível para determinados tipos de exceções.  
  
## Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)   
 [Práticas recomendadas para exceções](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Exception Handling](/visual-cpp/windows/exception-handling-cpp-component-extensions)