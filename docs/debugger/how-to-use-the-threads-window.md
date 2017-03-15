---
title: "Como usar a janela Threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.threads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "@TIB"
  - "depurador, Janela Threads"
  - "depurando [Visual Studio], threads"
  - "Função SetThreadName"
  - "Propriedade Thread.Name"
  - "threading [Visual Studio], depuração"
  - "Janela Threads"
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar a janela Threads
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Na janela **Threads**, você pode examinar e trabalhar com threads no aplicativo que você está depurando.  
  
 A janela **Threads** contém uma tabela onde cada linha representa um thread em seu aplicativo.  Por padrão, a tabela lista todos os threads em seu aplicativo, mas você pode filtrar a lista para mostrar apenas os threads do seu interesse.  Cada coluna contém um tipo diferente de informação.  Você também pode ocultar algumas colunas.  Se você exibir todas as colunas, as seguintes informações são exibidas, da esquerda para a direita:  
  
-   A coluna do sinalizador, em que você pode marcar um thread para o qual você deseja prestar atenção especial.  Para obter informações sobre como sinalizar um thread, consulte [Como sinalizar não sinalizar threads](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md).  
  
-   A coluna thread ativo, em que uma seta amarela indica um thread ativo.  Um contorno de uma seta indica o thread onde a execução interrompe no depurador.  
  
-   A coluna **ID**, que contém o número de identificação para cada thread.  
  
-   A coluna **ID Gerenciada**, que contém os números de identificação gerenciados para threads gerenciados.  
  
-   A coluna **Categoria**, que categoriza threads como threads da interface do usuário, manipuladores de chamada de procedimento remoto ou threads de trabalho.  Uma categoria especial identifica o thread principal do aplicativo.  
  
-   A coluna **Nome**, que identifica cada thread por nome, se tiverem um ou \<Sem nome\>.  
  
-   A coluna **Local**, que mostra onde o thread está sendo executado.  Você pode expandir este local para mostrar a pilha de chamadas inteira para o thread.  
  
-   A coluna **Prioridade**, que contém a prioridade ou precedência que o sistema atribuiu a cada thread.  
  
-   A coluna **Máscara de Afinidade**, que é uma coluna avançada que é normalmente oculta.  Esta coluna mostra a máscara de afinidade do processador para cada thread.  Em um sistema com vários processadores, a máscara de afinidade determina quais processadores em qual thread pode ser executado.  
  
-   A coluna **Contagem Suspensa**, que contém a contagem suspensa.  Esta contagem determina se um thread pode ser executado.  Para obter uma explicação de contagem suspensa, consulte “Congelando e descongelando threads” posteriormente neste tópico.  
  
-   A coluna **Nome do Processo**, que contém o processo ao qual cada thread pertence.  Esta coluna pode ser útil quando você estiver depurando vários processos, mas geralmente está oculta.  
  
### Para exibir a janela de threads no modo de interrupção ou no modo de execução  
  
-   No menu **Depurar**, aponte para **Windows** e, em seguida, clique em **Threads**.  
  
### Para exibir ou ocultar uma coluna  
  
-   Na barra de ferramentas na parte superior da janela **Threads**, clique em **Colunas** e, em seguida, marque ou desmarque o nome da coluna que você deseja exibir ou ocultar.  
  
### Para alternar o thread ativo  
  
-   Execute uma das seguintes etapas:  
  
    -   Clique duas vezes em qualquer thread.  
  
    -   Clique com o botão direito em um thread e clique em **Alternar para Thread**.  
  
         A seta amarela é exibida ao lado do novo thread ativo.  O contorno cinza de uma seta identifica o thread onde a execução interrompe no depurador.  
  
## Agrupando e classificando threads  
 Quando você agrupa threads, um título aparece na tabela para cada grupo.  O título contém uma descrição do grupo, como “Thread de trabalho” ou “Threads sem sinalização” e um controle de árvore.  Os threads de membro de cada grupo aparecem no cabeçalho do grupo.  Se você quiser ocultar os threads de membro para um grupo, poderá usar o controle de árvore para recolher o grupo.  
  
 Como o agrupamento tem precedência sobre a classificação, você poderá agrupar threads por categoria, por exemplo, e, em seguida, classificá\-los por ID dentro de cada categoria.  
  
#### Para classificar threads  
  
1.  Na barra de ferramentas na parte superior da janela **Threads**, clique no botão na parte superior de qualquer coluna.  
  
     Os threads agora são classificados pelos valores nessa coluna.  
  
2.  Se você quiser inverter a ordem de classificação, clique no mesmo botão novamente.  
  
     Os threads que apareceram na parte superior da lista agora aparecem na parte inferior.  
  
#### Para agrupar threads  
  
-   Na barra de ferramentas da janela **Threads**, clique na lista **Agrupar por** e, em seguida, clique nos critérios pelos quais você deseja agrupar threads.  
  
#### Para classificar threads dentro de grupos  
  
1.  Na barra de ferramentas na parte superior da janela **Threads**, clique na lista **Agrupar por** e, em seguida, clique nos critérios pelos quais você deseja agrupar threads.  
  
2.  Na janela **Threads**, clique no botão na parte superior de qualquer coluna.  
  
     Os threads agora são classificados pelos valores nessa coluna.  
  
#### Para expandir ou recolher todos os grupos  
  
-   Na barra de ferramentas na parte superior da janela **Threads**, clique em **Expandir grupos** ou **Recolher grupos**.  
  
## Pesquisando threads específicos  
 No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], você pode procurar threads que correspondem a uma cadeia de caracteres especificada.  Quando você procura threads na janela **Threads**, a janela exibe todos os threads que correspondem à cadeia de caracteres de pesquisa em qualquer coluna.  Essas informações incluem o local do thread que aparece na parte superior da pilha de chamadas na coluna **Local**.  Por padrão, no entanto, a pilha de chamadas inteira não é pesquisada.  
  
#### Para pesquisar threads específicos  
  
-   Na barra de ferramentas na parte superior da janela **Threads**, vá para a caixa **Pesquisar** e:  
  
    -   Digite uma cadeia de caracteres de pesquisa e pressione ENTER.  
  
         \- ou \-  
  
    -   Clique na lista suspensa ao lado da caixa **Pesquisar** e selecione uma cadeia de caracteres de pesquisa de uma pesquisa anterior.  
  
-   \(Opcional\) Para incluir a pilha de chamadas inteira na pesquisa, selecione **Pesquisar Pilha de Chamadas**.  
  
## Congelando e descongelando threads  
 Quando você congela um thread, o sistema não iniciará a execução do thread mesmo se os recursos estiverem disponíveis.  
  
 No código nativo, você pode suspender ou retomar threads chamando as funções do Windows `SuspendThread` e `ResumeThread` ou funções [CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md) e [CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md) do MFC.  Se você chamar `SuspendThread` ou `ResumeThread`, modifique a *contagem suspensa*, que aparece na janela **Threads**.  Porém, se você congelar ou descongelar um thread nativo, não alterará a contagem suspensa.  No código nativo, um thread não pode ser executado a menos que seja descongelado e tenha uma contagem suspensa de zero.  
  
 No código gerenciado, congelar ou descongelar um thread altera a contagem suspensa.  No código gerenciado, um thread congelado tem uma contagem suspensa de 1.  No código nativo, um thread congelado tem uma contagem suspensa de 0 a menos que o thread tenha sido suspenso por uma chamada `SuspendThread`.  
  
> [!NOTE]
>  Quando você depura uma chamada de código nativo para o código gerenciado, o código gerenciado é executado no mesmo thread físico que o código nativo que o chamou.  Suspender ou congelar o thread nativo também congela o código gerenciado.  
  
#### Para congelar ou descongelar a execução de um thread  
  
-   Na barra de ferramentas na parte superior da janela **Threads**, clique em **Congelar Threads** ou **Descongelar Threads**.  
  
     Essa ação afeta somente os threads que estão selecionados na janela **Threads**.  
  
## Exibindo threads sinalizados  
 Você pode sinalizar um thread ao qual você deseja dar atenção especial marcando\-o com um ícone na janela **Threads**.  Para obter mais informações, consulte [Como sinalizar não sinalizar threads](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md).  Na janela Threads, você pode optar por exibir todos os threads ou apenas os threads sinalizados.  
  
#### Para exibir somente threads sinalizados  
  
-   Escolha o botão de sinalizar no canto superior esquerdo da janela **Threads**.  
  
## Exibindo pilhas de chamadas de threads e alternando entre quadros  
 Em um programa de vários threads, cada thread tem sua própria pilha de chamadas.  A janela **Threads** fornece um modo conveniente de exibir essas pilhas.  
  
#### Para exibir a pilha de chamadas de um thread  
  
-   Na coluna **Local**, clique no triângulo invertido ao lado do local do thread.  
  
     O local é expandido para mostrar a pilha de chamadas para o thread.  
  
#### Para exibir ou recolher as chamadas de pilhas de todos os threads  
  
-   Na barra de ferramentas na parte superior da janela **Threads**, clique em **Expandir Pilhas de Chamadas** ou **Recolher Pilhas de Chamadas**.  
  
## Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Instruções passo a passo: depurando um aplicativo multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md)