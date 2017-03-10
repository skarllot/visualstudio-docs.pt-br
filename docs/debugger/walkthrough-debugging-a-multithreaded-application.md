---
title: "Instru&#231;&#245;es passo a passo: depurando um aplicativo multithread | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "depuração com multithread, passo a passo"
  - "explicações passo a passo, depuração com multithread"
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: depurando um aplicativo multithread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] fornece uma janela de **Threads** aprimorada e outras melhorias da interface de usuário para facilitar a depuração de aplicativos de vários threads.  Este passo a passo só levará alguns minutos e o ajudará a se familiarizar com os recursos da nova interface para depurar aplicativos de vários threads.  
  
 Para iniciar este passo a passo, você precisará de um projeto de aplicativo de vários threads.  Siga as etapas listadas aqui para criar o projeto.  
  
#### Para criar o projeto passo a passo  
  
1.  No menu **Arquivo**, escolha **Novo** e clique em **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Na caixa **Tipo de Projeto**, clique na linguagem de sua escolha: **Visual Basic**, **Visual C\#** ou **Visual C\+\+**.  
  
3.  Na caixa **Modelos**, escolha **Aplicativo de Console** ou **Aplicativo do Console CLR**.  
  
4.  Na caixa **Nome**, digite o nome MyThreadWalkthroughApp.  
  
5.  Clique em **OK**.  
  
     Um novo projeto de console é exibido.  Quando o projeto tiver sido criado, um arquivo de origem aparecerá.  Dependendo da linguagem escolhida, o arquivo de origem poderá ser chamado Module1.vb, Program.cs ou MyThreadWalkthroughApp.cpp  
  
6.  Exclua o código que aparece no arquivo de origem e substitua\-o pelo código de exemplo que aparece na seção “Criando um thread” do tópico [Criando threads e passando dados na hora de início](../Topic/Creating%20Threads%20and%20Passing%20Data%20at%20Start%20Time.md).  
  
7.  No menu **Arquivo**, clique em **Salvar Tudo**.  
  
#### Para iniciar o passo a passo  
  
-   Na janela de origem, procure o seguinte código:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```c#  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### Para iniciar a depuração  
  
1.  Clique com o botão direito na instrução `Console.WriteLine`, aponte para **Ponto de Interrupção** e clique em **Inserir Ponto de Interrupção**.  
  
     Na medianiz no lado esquerdo da janela de origem, uma bola vermelha aparece.  Isso indica que um ponto de interrupção agora está definido nesse local.  
  
2.  No menu **Depuração**, clique em **Iniciar Depuração**.  
  
     A depuração é iniciada, seu aplicativo de console começa a ser executado e, em seguida, para no ponto de interrupção.  
  
3.  Se a janela do aplicativo de console tiver o foco neste momento, clique na janela do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para retornar o foco para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Na janela de origem, localize a linha que contém o seguinte código:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```c#  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
#### Para descobrir o marcador de thread  
  
1.  Clique com o botão direito na janela **Threads**, clique em **Mostrar Threads em Origem**.  
  
2.  Examine a medianiz no lado esquerdo da janela.  Nessa linha, você verá um ícone semelhante a dois threads de pano.  Um thread é vermelho e o outro é azul.  O marcador de thread indica que um thread está parado nesse local.  Possivelmente, o thread está parado nesse local.  
  
3.  Passe o ponteiro sobre o marcador de thread.  Um DataTip que aparece.  O DataTip mostra o nome e o número de ID do thread para cada thread parado.  Nesse caso, há apenas um thread, cujo nome é provavelmente `<noname>`.  
  
4.  Clique com o botão direito no marcador de thread.  Observe as opções no menu de atalho.  
  
 Esse ícone é um *marcador de thread*:  
  
 ![Marcador de thread](../debugger/media/threadmarker.png "ThreadMarker")  
  
## Sinalizando e removendo a sinalização de threads  
 No [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)], você pode sinalizar os threads para os quais deseja dar atenção especial.  Sinalizar threads é uma boa maneira de manter o controle de threads importantes e ignorar threads com os quais você não precisa se preocupar.  
  
#### Para sinalizar threads  
  
1.  No menu **Exibir**, aponte para **Barras de Ferramentas**.  
  
     Verifique se a barra de ferramentas **Local de Depuração** está selecionada.  
  
2.  Vá para a barra de ferramentas **Local de depuração** e clique na lista **Thread**.  
  
    > [!NOTE]
    >  Você pode reconhecer essa barra de ferramentas por três listas importantes: **Processo**, **Thread** e **Registro de Ativação**.  
  
3.  Observe quantos threads aparecem na lista.  
  
4.  Volte à janela de origem e clique com o botão direito no marcador **Thread** novamente.  
  
5.  No menu de atalho, aponte para **Sinalizar** e clique no nome e no número de ID do thread.  
  
6.  Volte para a barra de ferramentas **Local de depuração** e clique na lista **Thread** novamente.  
  
     Somente o thread sinalizado agora aparece na lista.  O botão do sinalizador que está à direita da lista **Thread**.  O ícone de sinalizador no botão estava esmaecido antes.  Agora, é um vermelho contínuo e brilhante.  
  
7.  Passe o ponteiro sobre o ícone do sinalizador.  
  
     Um pop\-up será exibido.  Este popup informa em qual modo a lista **Thread** está: **Mostrar Somente Threads Sinalizados**.  
  
8.  Clique no botão de sinalizador para ativar\/desativar o modo **Mostrar Todos as Threads**.  
  
9. Clique na lista **Thread** novamente e verifique se você pode ver todos os threads novamente.  
  
10. Clique no botão de sinalizador para ativar\/desativar **Mostrar Somente Threads Sinalizados**.  
  
11. No menu **Depurar**, aponte para **Windows** e clique em **Threads**.  
  
     A janela **Threads** é exibida.  Um thread tem um ícone de sinalizador destacado anexado.  
  
12. Na janela de origem, clique com o botão direito no marcador de thread novamente.  
  
     Observe quais opções estão disponíveis no menu de atalho.  Em vez de **Sinalizar**, você agora verá **Remover Sinalização**.  Não clique em **Remover Sinalização**.  
  
13. Vá para o próximo procedimento sobre como remover a sinalização do thread.  
  
#### Para remover a sinalização de threads  
  
1.  Na janela **Threads**, clique com o botão direito na linha que corresponde ao thread sinalizado.  
  
     Um menu de atalho é exibido.  Ele tem opções para **Remover Sinalização** e **Remover Sinalização de Tudo**.  
  
2.  Para remover a sinalização do thread, clique em **Remover Sinalização**.  
  
3.  Clique no ícone de sinalizador vermelho.  
  
4.  Examine a barra de ferramentas **Local de depuração** novamente.  O sinalizador do botão ficará esmaecido novamente.  Você removerá a sinalização do único thread sinalizado.  Como não há nenhum thread sinalizado, a barra de ferramentas voltou para o modo **Mostrar Todos as Threads**.  Clique na lista **Thread** e verifique se você pode ver todos os threads.  
  
5.  Volte para a janela **Threads** e examine as colunas de informações.  
  
     Na parte superior de cada coluna, a maioria dos botões têm títulos que identificam a coluna.  No entanto, a primeira coluna à esquerda não tem título.  Em vez disso, tem um ícone, que é o contorno de um sinalizador.  Você observará o mesmo contorno em cada linha da lista de thread.  O contorno significa que a sinalização foi removida do thread.  
  
6.  Clique nos contornos do sinalizador para dois threads, o segundo e o terceiro da parte inferior da lista.  
  
     Os ícones de sinalizador ficam vermelho contínuo, em vez de contornos vazado.  
  
7.  Clique no botão na parte superior da coluna do sinalizador.  
  
     A ordem da lista de thread foi alterada quando você clicou no botão.  A lista de thread agora é classificada com os threads sinalizados na parte superior.  
  
8.  Novamente, clique no botão na parte superior da coluna do sinalizador.  
  
     A ordem de classificação foi modificada novamente.  
  
## Mais sobre a janela de threads  
  
#### Para saber mais sobre a janela de threads  
  
1.  Na janela **Threads**, examine a terceira coluna da esquerda.  No botão na parte superior dessa coluna, está escrito **ID**.  
  
2.  Clique em **ID**.  
  
     A lista de thread agora é classificada pelo número de identificação do thread.  
  
3.  Clique com o botão direito em qualquer thread na lista.  No menu de atalho, clique em **Exibição hexadecimal**.  
  
     O formato dos números da ID de thread é alterado.  
  
4.  Passe o ponteiro de mouse sobre qualquer thread na lista.  
  
     Depois de um atraso momentâneo, um DataTip é exibido.  Ele mostra uma pilha de chamadas parcial para o thread.  
  
5.  Examine a quarta coluna da esquerda, rotulada **Categoria**.  Os threads são classificados em categorias.  
  
     O primeiro thread criado em um processo é chamado de thread principal.  Localize\-o na lista de thread.  
  
6.  Clique com o botão direito no thread principal e clique em **Alternar para Thread**.  
  
     Aparece uma caixa de diálogo de aviso.  Ela indica que o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não pode exibir o código\-fonte do thread principal.  
  
     Clique em **OK**.  
  
7.  Observe a janela **Pilha de Chamadas** e a barra de ferramentas **Local de Depuração**.  
  
     O conteúdo da janela **Pilha de Chamadas** foi alterado.  
  
## Alternando o thread ativo  
  
#### Para alternar segmentos  
  
1.  Na janela **Threads**, examine a segunda coluna da esquerda.  O botão na parte superior dessa coluna não tem texto ou ícone.  Essa coluna é a coluna **Thread Ativo**.  
  
2.  Observe na coluna **Thread Ativo** que um thread tem uma seta amarela.  Esse é o *indicador de thread ativo*.  
  
3.  Anote o número de ID do thread onde o indicador de thread ativo está localizado.  Você moverá o indicador de thread ativo para outro thread, mas terá que colocá\-lo de volta onde terminou.  
  
4.  Clique com o botão direito no outro thread e clique em **Alternar para Thread**.  
  
5.  Observe a janela **Pilha de Chamadas** na janela de origem.  O conteúdo foi alterado.  
  
6.  Examine a barra de ferramentas **Local de Depuração**.  O thread ativo foi alterado lá também.  
  
7.  Vá para a barra de ferramentas **Local de Depuração**.  Clique na caixa **Thread** e escolha um thread diferente na lista suspensa.  
  
8.  Observe a janela **Threads**.  O indicador de thread ativo foi alterado.  
  
9. Na janela de origem, clique com o botão direito em u marcador de thread.  No menu de atalho, aponte para **Alternar para** e clique em um nome\/número de ID do thread.  
  
     Agora você viu três maneiras de alterar o thread ativo: usando a janela **Threads**, a caixa **Thread** na barra de ferramentas **Local de Depuração** e o indicador de thread na janela de origem.  
  
     Com o indicador de thread, você pode alternar somente para threads que pararam nesse local específico.  Usando a janela **Threads** e a barra de ferramentas **Local de Depuração**, você pode alternar para qualquer thread.  
  
## Congelando e descongelando a execução de thread  
  
#### Para congelar e descongelar threads  
  
1.  Na janela **Threads**, clique com o botão direito em qualquer thread e clique em **Congelar**.  
  
2.  Examine a coluna de thread ativo.  O par de barras verticais agora aparece ali.  Essas duas barras azuis indicam que o thread está congelado.  
  
3.  Examine a coluna **Suspender**.  A contagem de suspensão para o thread agora é 1.  
  
4.  Clique com o botão direito no thread congelado e clique em **Descongelar**.  
  
     A coluna do thread ativo e a coluna **Suspender** são alteradas.  
  
## Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como alternar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)