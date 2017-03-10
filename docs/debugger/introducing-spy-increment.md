---
title: "Introdu&#231;&#227;o a Spy++ | Microsoft Docs"
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
  - "Spy++"
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Introdu&#231;&#227;o a Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spy \+ \+ permite que você execute as seguintes tarefas:  
  
-   Exiba um gráfico de árvore de relações entre objetos do sistema. Eles incluem [processos](../debugger/processes-view.md), [threads](../debugger/threads-view.md), e [windows](../debugger/windows-view.md).  
  
-   Procurar especificado [windows](../debugger/how-to-search-for-a-window-in-windows-view.md), [threads](../debugger/how-to-search-for-a-thread-in-threads-view.md), [processos](../debugger/how-to-search-for-a-process-in-processes-view.md), ou [mensagens](../Topic/How%20to:%20Search%20for%20a%20Message%20in%20Messages%20View.md).  
  
-   Exibir as propriedades de selecionado [windows](../debugger/how-to-display-window-properties.md), [threads](../Topic/How%20to:%20Display%20Thread%20Properties.md), [processos](../debugger/how-to-display-process-properties.md), ou [mensagens](../debugger/how-to-display-message-properties.md).  
  
-   Selecione uma janela, thread, processo ou mensagem diretamente no modo de exibição.  
  
-   Use o [ferramenta localizador](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md) para selecionar uma janela, posicionamento do ponteiro do mouse.  
  
-   Definir [Opções de mensagem](_asug_choosing_message_options) usando parâmetros de seleção de log de mensagem complexos.  
  
 Spy \+ \+ tem uma barra de ferramentas e hiperlinks para ajudá\-lo a trabalhar mais rápido. Ele também fornece um **atualizar** comando para atualizar a exibição ativa, um **ferramenta de localização de janela** para tornar mais fácil, espionagem e um **fonte** caixa de diálogo para personalizar o windows de modo de exibição. Além disso, Spy \+ \+ permite salvar e restaurar as preferências do usuário.  
  
 Em vários Spy \+ \+ windows, clique para exibir um menu de atalho de comandos usados com frequência. Quais comandos são exibidos depende de onde está o ponteiro. Por exemplo, se clicar uma entrada na exibição da janela e a janela selecionada estiver visível, clique em **realçar** no atalho do menu faz com que a borda da janela selecionada para o flash para que possa ser localizado mais facilmente.  
  
> [!NOTE]
>  Há dois outros utilitários que se assemelham a Spy \+ \+: PView, que mostra detalhes sobre processos e threads e DDESPY. EXE, que permite que você monitore mensagens de Dynamic Data Exchange \(DDE\).  
  
## Sistemas operacionais de 64 bits  
 Há duas versões do Spy \+ \+. A primeira versão, denominada Spy \+ \+ \(spyxx.exe\) é projetada para exibir as mensagens enviadas para uma janela que está sendo executado em um processo de 32 bits. Por exemplo, o Visual Studio é executado em um processo de 32 bits. Portanto, você pode usar Spy \+ \+ para exibir as mensagens enviadas a **Solution Explorer**. Como a configuração padrão para a maioria das versões do Visual Studio é executado em um processo de 32 bits, a primeira versão do Spy \+ \+ é aquele que está disponível na **ferramentas** menu do Visual Studio.  
  
 A segunda versão, denominada Spy \+ \+ \(64 bits\) \(spyxx\_amd64.exe\) é projetada para exibir as mensagens enviadas para uma janela que está sendo executado em um processo de 64 bits. Por exemplo, em um sistema operacional de 64 bits, o bloco de notas é executado em um processo de 64 bits. Portanto, você pode usar Spy \+ \+ \(64 bits\) para exibir as mensagens enviadas para o bloco de notas. Spy \+ \+ \(64 bits\) geralmente está localizado em  
  
 .. \\*Pasta de instalação do visual Studio*\\Common7\\Tools\\spyxx\_amd64.exe.  
  
 Você pode executar qualquer versão do Spy \+ \+ diretamente da linha de comando.  
  
> [!NOTE]
>  Embora o Spy \+ \+ \(64 bits\) nome contém "amd", ele é executado em qualquer x64 sistema operacional Windows.  
  
## Consulte também  
 [Usando Spy\+\+](../debugger/using-spy-increment.md)   
 [Exibições do Spy\+\+](../debugger/spy-increment-views.md)   
 [Referência de Spy\+\+](../debugger/spy-increment-reference.md)