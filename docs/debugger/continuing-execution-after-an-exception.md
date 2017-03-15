---
title: "Continuando a execu&#231;&#227;o depois de uma exce&#231;&#227;o | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, exceções"
  - "tratamento de exceção, continuando a execução após"
  - "Caixa de diálogo Exceções"
  - "exceções, continuando a execução após"
  - "execução, continuando após uma exceção"
  - "código gerenciado, tratamento de exceção"
  - "exceções gerenciadas, continuando a execução após"
  - "execução de programa"
  - "programas, executando"
  - "threading [Visual Studio], continuando a execução após exceções"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Continuando a execu&#231;&#227;o depois de uma exce&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando o depurador interrompe a execução devido a uma exceção, uma caixa de diálogo é exibida.  Para o Visual Basic ou C\#, você verá a caixa de diálogo [Exception Assistant](../Topic/Exception%20Assistant.md) por padrão.  Para C\+\+, você verá a caixa de diálogo **Exceção** mais antiga.  Se você estiver usando o Visual Basic ou C\#, mas tiver desabilitado o **Assistente de Exceção** na caixa de diálogo **Opções**, verá a caixa de diálogo **Exceção**.  
  
 Quando a caixa de diálogo **Assistente de Exceção** ou **Exceção** aparece, você pode tentar corrigir o problema que causou a exceção.  
  
## Código gerenciado  
 No código gerenciado, você poderá continuar a execução no mesmo thread após uma exceção não tratada.  O **Assistente de Exceção** desenrola a pilha de chamadas até o ponto onde a exceção foi gerada.  
  
## Código nativo  
 No modo nativo C\/C\+\+, você tem duas opções:  
  
-   Você pode clicar em **Interromper** e tentar corrigir o problema.  Enquanto estiver no modo de interrupção, você poderá desenrolar a pilha de chamadas clicando com o botão direito em um quadro na janela **Pilha de Chamadas** e selecionar **Desenrolar para este Quadro** no menu de atalho.  Quando você continua a depuração, a caixa de diálogo **Exceção** aparecerá novamente se você não tiver solucionado o problema.  Caso contrário, a caixa de diálogo **Exceção** não reaparecerá.  
  
-   Você pode clicar em **Continuar** para continuar a execução sem tentar corrigir o problema.  A caixa de diálogo **Exceção** é reaberta.  
  
## Código misto  
 Se você atinge uma exceção não tratada ao depurar um código nativo misto e gerenciado, as restrições do sistema operacional impedem o desenrolar da pilha de chamadas.  Se você tentar voltar a pilha de chamadas usando o menu de atalho, uma mensagem de erro explicará que o depurador não pode desenrolar de uma exceção não tratada exceto durante a depuração de código misto.  
  
## Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)