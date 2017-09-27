---
title: "Começar a depurar aplicativos multithread | Microsoft Docs"
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
caps.latest.revision: 38
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
ms.openlocfilehash: 3ffb550707280d76756cbd144ed03f4143ce144b
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="get-started-debugging-a-multithreaded-application-in-visual-studio"></a>Começar a depuração de um aplicativo multithread no Visual Studio
Visual Studio fornece várias ferramentas e elementos de interface do usuário para ajudá-lo a depurar aplicativos multithread. Este tutorial mostra como usar marcadores de thread, o **pilhas paralelas** janela, o **inspeção paralela** janela pontos de interrupção condicionais e pontos de interrupção de filtro. Este tutorial leva apenas alguns minutos, mas concluí-la irá familiarizá-lo com os recursos para depurar aplicativos multithread.

|         |         |
|---------|---------|
| ![Assista a um vídeo](../install/media/video-icon.png "WatchVideo") | [Assista a um vídeo](#video) na depuração com multithread que mostra as etapas semelhantes. |

Outros tópicos fornecem informações adicionais sobre como usar outras ferramentas de depuração multithread:

- Para um tópico semelhante que mostra como usar o **local do depurador** barra de ferramentas e o **Threads** janela, consulte [passo a passo: depurar um aplicativo multithread](../debugger/how-to-use-the-threads-window.md).

- Para um tópico semelhante com um exemplo que usa <xref:System.Threading.Tasks.Task> (código gerenciado) e o tempo de execução de simultaneidade (C++), consulte [passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md). Para obter dicas de depuração gerais que se aplicam a tipos de aplicativos multithread mais, leia este tópico e o tópico vinculado.
  
Para iniciar este tutorial, você precisa de um projeto de aplicativo multi-threaded. Siga as etapas listadas aqui para criar o projeto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para criar o projeto de aplicativo multithread  
  
1.  Sobre o **arquivo** menu, escolha **novo** e, em seguida, clique em **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  No **tipo de projeto**s caixa, clique no idioma de sua escolha: **Visual C#**, **Visual C++**, ou **Visual Basic**.  
  
3.  No **modelos** caixa, escolha **aplicativo de Console**.  
  
4.  No **nome** caixa, digite o nome MyThreadWalkthroughApp.  
  
5.  Clique em **OK**.  
  
     Um novo projeto de console é exibido. Quando o projeto tiver sido criado, um arquivo de origem aparecerá. Dependendo do idioma escolhido, o arquivo de origem pode ser chamado Program.cs, MyThreadWalkthroughApp.cpp ou Module1. vb.  
  
6.  Excluir o código que aparece no arquivo de origem e substitua-o com o código de exemplo mostrado aqui.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
#### <a name="to-begin-the-tutorial"></a>Para começar o tutorial  
  
-   No editor de código fonte, procure o seguinte código: 
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Para iniciar a depuração  
  
1.  Clique na medianiz esquerda do `Thread.Sleep` ou `Thread::Sleep` instrução para inserir um novo ponto de interrupção.  
  
     Na medianiz no lado esquerdo do editor de código fonte, um círculo vermelho é exibido. Isso indica que um ponto de interrupção agora está definido nesse local. 
  
2.  Sobre o **depurar** menu, clique em **iniciar depuração** (**F5**).  
  
     O Visual Studio compila a solução, o aplicativo começa a ser executada com o depurador anexado e, em seguida, o aplicativo for interrompida no ponto de interrupção.  
  
    > [!NOTE]
    > Se você alternar o foco para a janela do console, clique no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela para retornar o foco para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  No editor de código fonte, localize a linha que contém o ponto de interrupção:  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Para descobrir o marcador de thread  

1.  Na barra de ferramentas Depurar, clique o **Mostrar Threads na origem** botão ![Mostrar Threads na origem](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Pressione **F11** uma vez para Avançar a linha de um do depurador de código.
  
3.  Examine a medianiz no lado esquerdo da janela. Nessa linha, você verá um *marcador de thread* ícone ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se parece com dois threads pano. O marcador de thread indica que um thread está parado nesse local.

    Observe que um marcador de thread pode ser parcialmente oculto por um ponto de interrupção. 
  
4.  Passe o ponteiro sobre o marcador de thread. Um DataTip aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado. Nesse caso, o nome é provavelmente `<noname>`. 
  
5.  Clique no marcador de thread para ver as opções disponíveis no menu de atalho.
    
## <a name="ParallelStacks"></a>Exibe o local de Threads

No **pilhas paralelas** janela, você pode alternar entre uma exibição de Threads e (para programação com base em tarefa) modo de exibição de tarefas e você pode exibir informações de pilha de chamada para cada thread. Neste aplicativo, podemos usar o modo de exibição de Threads.

1. Abra o **pilhas paralelas** janela escolhendo **Depurar > Windows > pilhas paralelas**. Você verá algo semelhante a este (a informação exata será diferente dependendo do local atual de cada thread, o hardware e a linguagem de programação).

    ![Janela de pilhas paralelas](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    Neste exemplo, da esquerda para direita obtemos essas informações:
    
    - O thread principal (lado esquerdo) foi interrompido no `Thread.Start` (o ponto de interrupção é indicado pelo ícone de marcador de thread ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Dois threads inseriu o `ServerClass.InstanceMethod`, um dos quais é o thread atual (seta amarela), enquanto o outro thread foi interrompido no `Thread.Sleep`.
    - Um novo thread (à direita) também está iniciando (interrompido em `ThreadHelper.ThreadStart`).

2.  Clique com botão direito entradas na **pilhas paralelas** janela para ver as opções disponíveis no menu de atalho.

    Você pode executar várias ações desses menus de atalho, mas para este tutorial mostraremos mais esses detalhes no **inspeção paralela** janela (próximas seções).

    > [!NOTE]
    > Se você está mais interessado em ver uma lista de exibir informações sobre cada thread, use o **Threads** janela em vez disso. Consulte [passo a passo: depurar um aplicativo multithread](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Definir uma inspeção em uma variável

1. Abra o **inspeção paralela** janela escolhendo **Depurar > Windows > inspeção paralela > paralela inspecionar 1**.

2. Clique na célula onde você pode ver o `<Add Watch>` texto (ou a célula de cabeçalho vazio na coluna 4º), tipo `data`, e pressione Enter.

    Os valores para a variável de dados para cada thread aparecem na janela.

3. Clique novamente na célula onde você pode ver o `<Add Watch>` texto (ou a célula de cabeçalho vazio na coluna 5), tipo `count`, e pressione Enter.

    Os valores para a variável de contagem para cada thread aparecem na janela. (Se você não ver essa quantidade de informações, pressione F11 mais algumas vezes para Avançar a execução de threads no depurador.)

    ![Janela Inspecionar paralelas](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Clique em uma das linhas na janela para exibir as opções disponíveis.

## <a name="flagging-and-unflagging-threads"></a>Sinalizando e removendo a sinalização de threads  
Você pode sinalizar threads para dar atenção especial. Sinalizar threads é uma boa maneira de controlar os threads importantes e ignorar threads que não faz sobre.  
  
#### <a name="to-flag-threads"></a>Para sinalizar threads  

1. No **inspeção paralela** janela, mantenha a tecla SHIFT pressionada e selecione várias linhas.

2. Clique com botão direito e escolha **sinalizador**.

    Agora, todos os threads sinalizados. Agora, você pode filtrar para mostrar somente threads sinalizados.
  
3.  No **inspeção paralela** janela, localize a **Mostrar somente Threads sinalizados** botão ![Mostrar Threads sinalizados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Clique o **Mostrar somente Threads sinalizados** botão.  
  
    Somente o thread sinalizado agora aparece na lista.

    > [!TIP]
    > Quando você sinalizou alguns threads, você pode clique uma linha de código no editor de código e escolha **executar Threads sinalizados Cursor** (certifique-se de que você escolha o código que todos os threads sinalizados alcançará). Isso irá pausar threads na linha selecionada de código, tornando mais fácil controlar a ordem de execução pelo [congelar e descongelar threads](#bkmk_freeze).

5.  Clique o **Mostrar somente Threads sinalizados** botão para voltar ao **Mostrar todos os Threads** modo.
    
#### <a name="to-unflag-threads"></a>Para remover a sinalização de threads

Para sinalizar threads, clique uma ou mais threads sinalizados no **inspeção paralela** janela e escolha **Unflag**.

## <a name="bkmk_freeze"></a>Congelar e descongelar a execução do thread 

> [!TIP]
> Você pode congelar e descongelar (suspender e retomar) threads para controlar a ordem na qual os threads executam trabalho. Isso pode ajudá-lo a resolver problemas de simultaneidade, como deadlocks e condições de corrida.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para congelar e descongelar threads  
  
1.  No **inspeção paralela** janela, com todas as linhas selecionadas, clique com botão direito e selecione **congelar**.

    Na segunda coluna, um ícone de pausar agora é exibido para cada linha. O ícone de pausa indica que o thread está congelado.

2.  Desmarque as linhas clicando em apenas uma linha.

3.  Clique em uma linha e selecione **descongelar**.

    O ícone de pausar desaparece nesta linha, que indica que o thread não está congelado.

4.  Alterne para o editor de código e clique em **F11**. Executa somente o thread não congelado.

    O aplicativo também pode criar uma instância de alguns novos threads. Observe que quaisquer novos threads são sem sinalizador e não estão congelados.

## <a name="bkmk_follow_a_thread"></a>Execute um único Thread usando pontos de interrupção condicionais

Às vezes, pode ser útil acompanhar a execução de um único thread no depurador. Uma forma que você pode fazer isso é congelando threads que não estão interessados em, mas em alguns cenários, talvez seja conveniente seguir um único thread sem congelamento de outros threads (para reprodução de um determinado erro, por exemplo). Para seguir um segmento sem congelamento de outros threads, você deve evitar dividir em código, exceto no thread que você está interessado. Você pode fazer isso definindo uma [ponto de interrupção condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Você pode definir pontos de interrupção em diferentes condições, como o nome do thread ou a ID do thread. Outro método que pode ser útil é definir a condição nos dados que você sabe que serão exclusivos para cada thread. Este é um cenário comum de depuração, no qual você está mais interessado em alguns valores de dados específico que em qualquer thread específico.

#### <a name="to-follow-a-single-thread"></a>A seguir um único thread

1. Clique com botão direito no ponto de interrupção que você criou anteriormente e escolha **condições**.

2. No **configurações de ponto de interrupção** , digite `data == 5` para a expressão condicional.

    ![Ponto de interrupção condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Se você está mais interessado em um segmento específico, use um nome de thread ou a ID do thread para a condição. Para fazer isso no **configurações de ponto de interrupção** janela, selecione **filtro** em vez de **expressão condicional**e siga as dicas de filtro. Talvez você queira nomear seus threads no código do aplicativo (como segmentos IDs alterar quando você reiniciar o depurador).

3. Fechar o **configurações de ponto de interrupção** janela.

4. Clique a reinicialização ![aplicativo reiniciar](../debugger/media/dbg-tour-restart.png "RestartApp") botão reiniciar a sessão de depuração.

    Você interromperá em código no thread para o qual a variável de dados é 5. Examinar a seta amarela (contexto do depurador atual) a **inspeção paralela** janela para verificar se.

5. Agora, passar por código (F10) e entrar no código (F11) e acompanhar a execução de thread único.

    Desde que a condição de ponto de interrupção é exclusiva para o thread, e o depurador não ocorrências de qualquer outro ponto de interrupção em outros threads (talvez seja necessário desabilitá-las), você pode percorrer o código e entrar no código sem alternar para outro thread.

    > [!NOTE]
    > Quando você avança o depurador, todos os threads serão executados. No entanto, o depurador não entrará no código em outros threads, a menos que um dos outros threads atinge um ponto de interrupção. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Mais informações sobre janelas de depuração com multithread 

#### <a name="to-switch-to-another-thread"></a>Para alternar para outro thread 

- Para alternar para outro thread, consulte [como: alternar para outro Thread enquanto depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

## <a name="video"></a>Assista a um vídeo sobre a depuração com multithread

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171" frameborder="0" allowfullscreen></iframe>
</div>

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Para saber mais sobre as janelas de pilha paralelo e inspeção paralela  
  
- Consulte [como: usar a janela de pilha paralela](../debugger/using-the-parallel-stacks-window.md) 

- Consulte [como: usar a janela Inspeção paralela](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como mudar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)

