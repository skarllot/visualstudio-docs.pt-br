---
title: "Como depurar em um cluster de alto desempenho | Microsoft Docs"
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
  - "depuração de cluster"
  - "depuração de alto desempenho"
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar em um cluster de alto desempenho
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A depuração de um programa com vários processamentos em um cluster de alto desempenho é semelhante à depuração de um programa comum em um computador remoto.  No entanto, há algumas considerações adicionais.  Para requisitos gerais de configuração remota, consulte [Depuração remota](../debugger/remote-debugging.md).  
  
 Ao depurar em um cluster de alto desempenho, você pode usar todas as janelas e técnicas de depuração do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que estiverem disponíveis para a depuração remota.  Como você está depurando remotamente, no entanto, a janela do console externo não está disponível.  
  
 A janela **Threads** e a janela **Processos** são úteis especificamente para depurar aplicativos paralelos.  Para obter dicas sobre como usar essas janelas, consulte [How to: Use the Processes Window](http://msdn.microsoft.com/pt-br/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) e [Como usar a janela Threads](../debugger/how-to-use-the-threads-window.md).  
  
 Os procedimentos a seguir mostram algumas técnicas que são muito úteis para depurar em um conjunto de alto desempenho.  
  
 Ao depurar um aplicativo paralelo, convém definir um ponto de interrupção em um segmento, processo, ou em um computador específico.  Você pode fazer isso criando um ponto de interrupção normal, e depois adicionando um filtro de ponto de interrupção.  
  
### Para abrir a caixa de diálogo Filtro de Ponto de Interrupção  
  
1.  Clique com o botão direito em um glifo de ponto de interrupção em uma janela de origem, na janela de **Desmontagem**, na janela de **Pilha de Chamadas** ou na janela de **Pontos de Interrupção**.  
  
2.  No menu de atalho, clique em **Filtrar**.  Essa opção pode aparecer no nível superior ou no submenu em **Pontos de Interrupção**.  
  
### Para definir um ponto de interrupção em um computador específico  
  
1.  Obter o nome do computador na janela **Processos**.  
  
2.  Selecione um ponto de interrupção e abra a caixa de diálogo **Filtro de Ponto de Interrupção** como descrito no procedimento anterior.  
  
3.  Na caixa de diálogo **Filtro de Ponto de Interrupção**, digite:  
  
     MachineName \=*yourmachinename*  
  
     Para criar um filtro mais complexo, você pode combinar cláusulas usando `&`, o operador AND, `||`, o operador OR, `!`, o operador NOT, e parênteses.  
  
4.  Clique em **OK**.  
  
### Para definir um ponto de interrupção em um processo específico  
  
1.  Obter o nome do processo ou o número do ID do processo na janela **Processos**.  
  
2.  Selecione um ponto de interrupção e abra a caixa de diálogo **Filtro de Ponto de Interrupção** como no primeiro procedimento.  
  
3.  Na caixa de diálogo **Filtro de Ponto de Interrupção**, digite:  
  
     `ProcessName =`  *yourprocessname*  
  
     —ou—  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Para criar um filtro mais complexo, você pode combinar cláusulas usando `&`, o operador AND, `||`, o operador OR, `!`, o operador NOT, e parênteses.  
  
4.  Clique em **OK**.  
  
### Para definir um ponto de interrupção em um segmento específico  
  
1.  Obter o nome do thread ou o número do ID do thread na janela **Threads**.  
  
2.  Selecione um ponto de interrupção e abra a caixa de diálogo **Filtro de Ponto de Interrupção** como descrito no primeiro procedimento.  
  
3.  Na caixa de diálogo **Filtro de Ponto de Interrupção**, digite:  
  
     `ThreadName =` *yourthreadname*  
  
     —ou—  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Para criar um filtro mais complexo, você pode combinar cláusulas usando `&`, o operador AND, `||`, o operador OR, `!`, o operador NOT, e parênteses.  
  
4.  Clique em **OK**.  
  
## Exemplo  
 O exemplo a seguir mostra como criar um filtro para um ponto de interrupção em um computador chamado `marvin` e um thread chamado `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuração remota](../debugger/remote-debugging.md)   
 [How to: Use the Processes Window](http://msdn.microsoft.com/pt-br/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Como usar a janela Threads](../debugger/how-to-use-the-threads-window.md)   
 [Threads and Processes](http://msdn.microsoft.com/pt-br/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)