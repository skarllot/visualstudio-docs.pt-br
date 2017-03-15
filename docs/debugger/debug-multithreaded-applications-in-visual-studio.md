---
title: "Depurar aplicativos multithread no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], computação de alto desempenho"
  - "depurando [Visual Studio], com multithread"
  - "depuração de alto desempenho"
  - "depuração com multithread"
  - "threading [Visual Studio], depuração"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar aplicativos multithread no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um thread é uma sequência de instruções para que o sistema operacional aloque tempo no processador.  Cada processo que está em execução no sistema operacional consiste em pelo menos um thread.  Os processos que têm mais de um thread são chamados multithread.  
  
 Os computadores com vários processadores, processadores de vários núcleos ou processos de hyperthreading podem executar vários threads ao mesmo tempo.  O processamento paralelo de vários threads pode aumentar melhorar o desempenho do programa, mas também pode tornar a depuração mais difícil porque apresenta a necessidade de manter controle de vários threads.  
  
 Além disso, o multithreading apresenta alguns novos tipos de bugs potenciais.  Geralmente, dois ou mais threads precisam acessar o mesmo recurso, mas apenas um thread pode acessar com segurança o recurso de cada vez.  Alguma forma de exclusão mútua é necessário para certificar\-se de que apenas um thread está acessando o recurso de cada vez.  Se a exclusão mútua for executada incorretamente, ela poderá criar uma condição *deadlock* em que nenhum thread poderá ser executado.  Deadlocks podem ser um problema particularmente difícil de depurar.  
  
 O Visual Studio fornece um**Threads**janela, uma janela de Threads da GPU, uma janela de inspeção paralela e outros recursos que tornam a depuração de vários segmentos. A melhor maneira de aprender sobre os recursos de threads é seguindo as orientações.  Consulte[Instruções passo a passo: depurando um aplicativo multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md)e[Instruções passo a passo: depurando um aplicativo C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md).  
  
 O Visual Studio também fornece os pontos de interrupção avançados e pontos de controle, que podem ser muito úteis quando você depura aplicativos multissegmentados.  Você pode usar filtros de ponto de interrupção para incluir pontos de interrupção em threads individuais.  Consulte[Usando pontos de interrupção](../debugger/using-breakpoints.md)  
  
 Depurar um aplicativo com vários thread que tenha uma interface de usuário pode ser especialmente difícil.  Nesse caso, você poderá considerar a execução do aplicativo em um segundo computador e o uso da depuração remota.  Para obter informações, consulte[Depuração remota](../debugger/remote-debugging.md).  
  
## Nesta seção  
 [Depurar threads e processos](../debugger/debug-threads-and-processes.md)  
 Explica os conceitos básicos de depuração de segmentos e processos.  
  
 [Depurar processos](../debugger/debug-multiple-processes.md)  
 Explica como depurar vários processos.  
  
 [Como usar a janela Threads](../debugger/how-to-use-the-threads-window.md)  
 Os procedimentos úteis para depurar segmentos com a janela **Threads**.  
  
 [Como alternar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Três maneiras para alternar o contexto de depuração para outro segmento.  
  
 [Como sinalizar não sinalizar threads](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md)  
 Marque ou sinalize threads aos quais você deseja dar atenção especial durante a depuração.  
  
 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Atribua ao thread um nome que seja exibido na janela **Threads**.  
  
 [Como definir um nome de thread no código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Atribua ao thread um nome que seja exibido na janela **Threads**.  
  
 [Instruções passo a passo: depurando um aplicativo multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Um tour guiado dos recursos de depuração com ênfase nos recursos para [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 [Como depurar em um cluster de alto desempenho](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Técnicas para depurar um aplicativo executado em um conjunto de alto desempenho.  
  
 [Dicas para threads de depuração no código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Técnicas simples que podem ser úteis para depurar threads nativos.  
  
 [Usando a janela Tarefas](../debugger/using-the-tasks-window.md)  
 Mostra uma lista de todos os objetos gerenciados ou nativos da tarefa que incluem seu status e outras informações úteis.  
  
 [Usando a janela Pilhas Paralelas](../debugger/using-the-parallel-stacks-window.md)  
 Mostra pilhas de chamadas de vários threads \(ou de tarefas\) em uma única exibição e também agrega os segmentos de pilha que são comuns entre segmentos \(ou tarefas\).  
  
 [Instruções passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)  
 A explicação passo a passo mostra como usar a janela Pilhas Paralelas e a janela Tarefas Paralelas.  
  
 [Como usar a janela Inspeção Paralela](../debugger/how-to-use-the-parallel-watch-window.md)  
 Inspecione valores e expressões em vários threads.  
  
 [Como usar a janela Threads de GPU](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
 Examinar e trabalhar com threads que estão em execução no GPU durante a depuração.  
  
## Seções relacionadas  
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)  
 -   Use filtros de ponto de interrupção quando você deseja colocar um ponto de interrupção em um segmento individual.  
  
-   Os pontos de controle permitem que você rastreie a execução do programa sem interrupções.  Isso pode ser útil para estudar problemas, como deadlocks.  
  
 [Threading](../Topic/Managed%20Threading.md)  
 Conceitos de segmentação na programação de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], incluindo o código de exemplo.  
  
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)  
 Como usar multithreading em componentes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Suporte multithread para código anterior \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Conceitos de segmentação e código de exemplo para programadores de C\+\+ que usam o MFC.  
  
## Consulte também  
 [Depurar threads e processos](../debugger/debug-threads-and-processes.md)   
 [Depuração remota](../debugger/remote-debugging.md)