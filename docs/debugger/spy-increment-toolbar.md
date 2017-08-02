---
title: "Barra de ferramentas do Spy++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barra de ferramentas Spy++"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Barra de ferramentas do Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A barra de ferramentas é exibida abaixo da barra de menu no Spy \+ \+.  Para exibir ou ocultar a barra de ferramentas, no  **Exibir** menu, clique em  **barra de ferramentas**.  
  
 Os seguintes controles estão disponíveis na barra de ferramentas.  
  
## Lista UIElement  
  
|Button|Efeito|  
|------------|------------|  
|![Botão do Windows Spy &#43; &#43;](~/debugger/media/icon_spy--_windows.gif "Icon\_Spy\+\+\_Windows")|Exibe uma visualização em árvore das janelas e controles no sistema.  Para obter mais informações, consulte [Exibição de janelas](../debugger/windows-view.md).|  
|![Botão de processos Spy &#43; &#43;](~/debugger/media/icon_spy--_processes.gif "Icon\_Spy\+\+\_Processes")|Exibe uma visualização em árvore dos processos no sistema.  Para obter mais informações, consulte [Exibição de processos](../debugger/processes-view.md).|  
|![Botão de Threads Spy &#43; &#43;](~/debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|Exibe uma visualização em árvore dos threads no sistema.  Para obter mais informações, consulte [Exibição de threads](../debugger/threads-view.md).|  
|![Botão de mensagens Spy &#43; &#43;](~/debugger/media/icon_spy--_messages.gif "Icon\_Spy\+\+\_Messages")|Cria uma janela para exibir mensagens de janela e abre o  **Opções de mensagem** caixa de diálogo para que você possa selecionar a janela cujas mensagens serão exibidas e também selecionar outras opções.  Para obter mais informações, consulte [Exibição de mensagens](../debugger/messages-view.md).|  
|![Botão de Log do Spy &#43; &#43; iniciar](~/debugger/media/icon_spy--_startlog.gif "Icon\_Spy\+\+\_StartLog")|Inicia o log de mensagens e exibe o fluxo de mensagens.  Este controle está disponível apenas quando um  **mensagens** janela é a janela ativa.  Para obter mais informações, consulte [Como iniciar e parar a exibição do log de mensagem](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy &#43; &#43; parar botão Log](~/debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|Paradas de mensagem de log e a exibição de fluxo de mensagens.  Este controle está disponível apenas quando um  **mensagens** janela é a janela ativa.  Para obter mais informações, consulte [Como iniciar e parar a exibição do log de mensagem](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botão de opções de Log Spy &#43; &#43;](~/debugger/media/icon_spy--_logoptions.gif "Icon\_Spy\+\+\_LogOptions")|Exibe o  [Opções de mensagem](../debugger/message-options-dialog-box.md) caixa de diálogo.  Use essa caixa de diálogo para selecionar o windows e tipos para exibição de mensagem.  Este controle está disponível apenas quando um  **mensagens** janela é a janela ativa.|  
|![Botão de limpar o registro do Spy &#43; &#43;](~/debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|Limpa o conteúdo do ativo  **mensagens** janela.  Este controle está disponível apenas quando um  **mensagens** janela é a janela ativa.|  
|![Botão da janela Localizar Spy &#43; &#43;](~/debugger/media/icon_spy--_findwindow.gif "Icon\_Spy\+\+\_FindWindow")|Abre o  [Janela Localizar](../debugger/find-window-dialog-box.md) caixa de diálogo que lhe permite definir os critérios de pesquisa de janela e exibir mensagens ou propriedades.  Para obter mais informações, consulte [Como usar a ferramenta Localizador](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md).|  
|![Spy &#43; &#43; localizar o primeiro botão da janela](~/debugger/media/icon_spy--_window.gif "Icon\_Spy\+\+\_Window")|Pesquisa o modo de exibição atual para uma janela correspondente, processo, thread ou mensagem.|  
|![Spy &#43; &#43; botão Localizar próxima janela](~/debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|Pesquisa o modo de exibição atual para a próxima janela correspondente, processo, thread ou mensagem.  Esse controle \(e o comando de menu relacionado\) estão disponíveis somente quando houver um resultado de pesquisa válido que não é exclusivo.  Por exemplo, quando você usa um identificador de janela como o critério de pesquisa na árvore de janela, ela produz resultados exclusivos porque há apenas uma janela na árvore de janela que tem esse identificador; Nesse exemplo,  **Localizar próxima** não está disponível.|  
|![Spy &#43; &#43; anterior janela botão Localizar](~/debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|Pesquisa o modo de exibição atual para a janela correspondente anterior, processo, thread ou mensagem.  Esse controle \(e o comando de menu relacionado\) estão disponíveis somente quando houver um resultado de pesquisa válido que não é exclusivo.  Por exemplo, quando você usa um identificador de janela como o critério de pesquisa na árvore de janela, ela produz resultados exclusivos porque há apenas uma janela na árvore de janela que tem esse identificador; Nesse exemplo,  **Localizar anterior** não está disponível.|  
|![Botão de Explorer propriedade Spy &#43; &#43;](~/debugger/media/icon_spy--_propexp.gif "Icon\_Spy\+\+\_PropExp")|Exibe as propriedades da janela que está selecionado no modo de exibição do Windows.|  
|![Botão de atualizar Spy &#43; &#43;](~/debugger/media/icon_spy--_refresh.gif "Icon\_Spy\+\+\_Refresh")|Atualiza as exibições do sistema.|  
  
## Consulte também  
 [Usando Spy\+\+](../debugger/using-spy-increment.md)   
 [Exibições do Spy\+\+](../debugger/spy-increment-views.md)   
 [Referência de Spy\+\+](../debugger/spy-increment-reference.md)