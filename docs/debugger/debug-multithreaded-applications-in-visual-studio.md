---
title: Depurar aplicativos multithread no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: c5a123ccb276e01953b2168d50e0d633640d384a
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicativos multithread no Visual Studio
Um thread é uma sequência de instruções para que o sistema operacional aloque tempo no processador. Cada processo que está em execução no sistema operacional consiste em pelo menos um thread. Os processos que têm mais de um thread são chamados multithread.  
  
Os computadores com vários processadores, processadores de vários núcleos ou processos de hyperthreading podem executar vários threads ao mesmo tempo. O processamento paralelo de vários threads pode aumentar melhorar o desempenho do programa, mas também pode tornar a depuração mais difícil porque apresenta a necessidade de manter controle de vários threads.  
  
Além disso, o multithreading apresenta alguns novos tipos de bugs potenciais. Geralmente, dois ou mais threads precisam acessar o mesmo recurso, mas apenas um thread pode acessar com segurança o recurso de cada vez. Alguma forma de exclusão mútua é necessário para certificar-se de que apenas um thread está acessando o recurso de cada vez. Se a exclusão mútua é executada incorretamente, ele poderá criar um *deadlock* condição em que nenhum thread pode ser executado. Deadlocks podem ser um problema particularmente difícil de depurar.

Visual Studio fornece ferramentas diferentes para uso na depuração de aplicativos multithread.

- Para threads, são as principais ferramentas para threads de depuração a **Threads** janela, marcadores de thread no windows de origem, **pilhas paralelas** janela, **inspeção paralela** janela, e o **local do depurador** barra de ferramentas. Para saber mais sobre o **Threads** janela e **local do depurador** barra de ferramentas, consulte [passo a passo: depurar usando a janela Threads](../debugger/how-to-use-the-threads-window.md). Para saber como usar o **pilhas paralelas** e **inspeção paralela** windows, consulte [começar a depuração de um aplicativo multithread](../debugger/get-started-debugging-multithreaded-apps.md). Os dois tópicos mostram como usar marcadores de thread.
  
- Para o código que usa o [tarefa TPL (biblioteca paralela)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou [tempo de execução de simultaneidade](/cpp/parallel/concrt/concurrency-runtime/), as principais ferramentas de depuração são o **pilhas paralelas** janela, o **Inspeção paralela** janela e o **tarefas** janela (a **tarefas** janela também oferece suporte a JavaScript). Para começar, consulte [passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) e [passo a passo: depurando um aplicativo C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application.md). 

- Para threads de depuração na GPU, a principal ferramenta é o **Threads de GPU** janela. Consulte [como: usar a janela Threads de GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Para processos, são as principais ferramentas de **anexar ao processo** caixa de diálogo, o **processos** janela e o **local do depurador** barra de ferramentas.  
  
O Visual Studio também fornece os pontos de interrupção avançados e pontos de controle, que podem ser muito úteis quando você depura aplicativos multissegmentados. Você pode usar condições de ponto de interrupção e filtros para colocar pontos de interrupção em segmentos individuais. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md). 
  
Depurar um aplicativo com vários thread que tenha uma interface de usuário pode ser especialmente difícil. Nesse caso, você poderá considerar a execução do aplicativo em um segundo computador e o uso da depuração remota. Para obter informações, consulte [depuração remota](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>Nesta seção
 [Começar a depuração de um aplicativo multithread](../debugger/get-started-debugging-multithreaded-apps.md).  
 Um tour interativo do thread de recursos, com ênfase nos recursos de depuração a **pilhas paralelas** janela e **inspeção paralela** janela.

 [Ferramentas de depuração de processos e Threads](../debugger/debug-threads-and-processes.md)  
 Lista os recursos das ferramentas de depuração de threads e processos.  
  
 [Depurar vários processos](../debugger/debug-multiple-processes.md)  
 Explica como depurar vários processos.

 [Passo a passo: Depurar usando a janela Threads](../debugger/how-to-use-the-threads-window.md).  
 Instruções passo a passo que mostra como usar o **Threads** janela e **local do depurador** barra de ferramentas. 

 [Passo a passo: Depurar um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Instruções passo a passo que mostra como usar o **pilhas paralelas** e **tarefas** windows.  
  
 [Como mudar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Três maneiras para alternar o contexto de depuração para outro segmento.  
  
 [Como sinalizar e remover sinalizador de threads](../debugger/how-to-flag-and-unflag-threads.md)  
 Marque ou sinalize threads aos quais você deseja dar atenção especial durante a depuração.    
  
 [Como depurar em um cluster de alto desempenho](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Técnicas para depurar um aplicativo executado em um conjunto de alto desempenho.  

 [Dicas para threads de depuração no código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Técnicas simples que podem ser úteis para depurar threads nativos. 

 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Nomeie o thread que aparecem no **Threads** janela.  
  
 [Como definir um nome de thread em código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Nomeie o thread que aparecem no **Threads** janela. 
  
## <a name="related-sections"></a>Seções relacionadas  
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)

 - Use filtros ou condições de ponto de interrupção quando quiser depurar um thread individual.  
  
 - Os pontos de controle permitem que você rastreie a execução do programa sem interrupções. Isso pode ser útil para estudar problemas, como deadlocks.  
  
 [Threading](/dotnet/standard/threading/index)  
 Conceitos de segmentação na programação de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], incluindo o código de exemplo.  
  
 [Multithreading em componentes](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Como usar multithreading em componentes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Suporte de multithreading para código anterior (Visual C++)](/cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Conceitos de segmentação e código de exemplo para programadores de C++ que usam o MFC.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar Threads e processos](../debugger/debug-threads-and-processes.md)   
 [Depuração remota](../debugger/remote-debugging.md)
