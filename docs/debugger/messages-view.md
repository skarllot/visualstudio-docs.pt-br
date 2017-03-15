---
title: "Exibi&#231;&#227;o de mensagens | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.messagesview"
helpviewer_keywords: 
  - "exibição Mensagens"
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de mensagens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cada janela possui um fluxo de mensagem associada.  Uma janela de exibição de mensagens exibe este fluxo de mensagens.  O identificador de janela, o código da mensagem e a mensagem são mostrados.  Você pode criar um modo de exibição de mensagens para um thread ou processo também.  Isso permite que você exibir mensagens enviadas para todas as janelas pertencentes a um determinado processo ou thread, que é particularmente útil para a captura de mensagens de inicialização da janela.  
  
 Uma janela típica de modo de exibição de mensagens é exibida abaixo.  Observe que a primeira coluna contém o identificador de janela e a segunda coluna contém um código de mensagem \(explicado em  [Códigos de mensagem](../debugger/message-codes.md)\).  Mensagem decodificada parâmetros e valores de retorno estão à direita.  
  
 ![Exibição de mensagens Spy &#43; &#43;](../debugger/media/spy--_messagesview.png "Spy\+\+\_MessagesView")  
Exibição de mensagens Spy \+ \+  
  
## Procedimentos  
  
#### Para abrir um modo de exibição de mensagens para uma janela, processo ou thread  
  
1.  Mover o foco para um  [De exibição do Windows](../debugger/windows-view.md),  [o modo de exibição de processos](../debugger/processes-view.md), ou  [Visualização de Threads](../debugger/threads-view.md) janela.  
  
2.  Localizar o nó para o item cujas mensagens você deseja examinar e selecioná\-lo.  
  
3.  Do  **Spy** menu, escolha  **Mensagens de Log**.  
  
     O  [Caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md) abre.  
  
4.  Selecione as opções para a mensagem que você deseja exibir.  
  
5.  Pressione  **OK** para começar as mensagens de log.  
  
     Uma abre a janela de exibição de mensagens e uma  **mensagens** menu é adicionado à barra de ferramentas Spy \+ \+.  Dependendo das opções selecionadas, mensagens de iniciar o fluxo contínuo para a janela ativa de modo de exibição de mensagens.  
  
6.  Quando você tem suficiente mensagens, escolha  **Parar registro** partir do  **mensagens** menu.  
  
## Nesta seção  
 [Controlando o modo de exibição de mensagens](../debugger/how-to-control-messages-view.md)  
 Explica como gerenciar o modo de exibição de mensagens.  
  
 [Modo de exibição de mensagens de abertura da janela Localizar](_asug_choosing_message_options)  
 Explica como abrir o modo de exibição de mensagens da caixa de diálogo de janela Localizar.  
  
 [Procurando por uma mensagem no modo de exibição de mensagens](../Topic/How%20to:%20Search%20for%20a%20Message%20in%20Messages%20View.md)  
 Explica como localizar uma mensagem específica no modo de exibição de mensagens.  
  
 [Iniciar e interromper a exibição de Log de mensagem](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Explica como iniciar e parar o log de mensagens.  
  
 [Códigos de mensagem](../debugger/message-codes.md)  
 Define os códigos para mensagens listadas no modo de exibição de mensagens.  
  
 [Exibindo propriedades de mensagem](../debugger/how-to-display-message-properties.md)  
 Como mostrar mais informação sobre uma mensagem.  
  
## Seções relacionadas  
 [Modos de exibição Spy \+ \+](../debugger/spy-increment-views.md)  
 Explica as exibições de árvore Spy \+ \+ do windows, mensagens, processos e threads.  
  
 [Usando o Spy \+ \+](../debugger/using-spy-increment.md)  
 Apresenta a ferramenta Spy \+ \+ e explica como ele pode ser usado.  
  
 [Caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md)  
 Usado para selecionar quais mensagens são listadas no modo de exibição de mensagens ativo.  
  
 [Caixa de diálogo de pesquisa de mensagem](../debugger/message-search-dialog-box.md)  
 Usado para localizar o nó de uma mensagem específica no modo de exibição de mensagens.  
  
 [Caixa de diálogo de propriedades de mensagem](../debugger/message-properties-dialog-box.md)  
 Usado para exibir as propriedades de uma mensagem selecionada no modo de exibição de mensagem.  
  
 [Referência Spy \+ \+](../debugger/spy-increment-reference.md)  
 Inclui seções descrevendo cada Spy \+ \+ menu e a caixa de diálogo caixa.