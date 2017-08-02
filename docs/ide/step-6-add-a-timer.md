---
title: 'Etapa 6: Adicionar um temporizador | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 21
author: kempb
ms.author: kempb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 996ec0a9fa601517993cb6049a114796c36489fe
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="step-6-add-a-timer"></a>Etapa 6: Adicionar um temporizador
Em seguida, adicione um controle **Timer** ao jogo de correspondência. Um temporizador aguarda um número especificado de milissegundos e, em seguida, dispara um evento, conhecido como um *tique*. Isso é útil para iniciar uma ação, ou repetir uma ação, regularmente. Nesse caso, você usará um temporizador para permitir que os jogadores escolham dois ícones e, se os ícones não corresponderem, ocultar os dois ícones novamente após um curto período.  
  
### <a name="to-add-a-timer"></a>Para adicionar um temporizador  
  
1.  Na caixa de ferramentas do Designer de Formulários do Windows, escolha **Temporizador** (na categoria **Componentes**) e escolha a tecla ENTER ou clique duas vezes no temporizador para adicionar um controle de temporizador ao formulário. O ícone do temporizador, chamado **Timer1**, deve ser exibido em um espaço abaixo do formulário, como mostra na imagem a seguir.  
  
     ![Timer](~/docs/ide/media/express_timer.png "Express_Timer")  
Temporizador  
  
    > [!NOTE]
    >  Se a caixa de ferramentas estiver vazia, você deve selecionar o designer de formulário, e não o código por trás do formulário, antes de abrir a caixa de ferramentas.  
  
2.  Escolha o ícone **Timer1** para selecionar o temporizador. Na janela **Propriedades**, mude do modo de exibição de eventos para o de propriedades. Em seguida, defina a propriedade **Intervalo** do temporizador como **750**, mas deixe a propriedade **Habilitado** definida como **Falso**. A propriedade **Intervalo** informa ao temporizador quanto tempo ele deve aguardar entre os *tiques* ou quando ele dispara seu evento Tick. Um valor de 750 informa ao temporizador para aguardar três quartos de um segundo (750 milissegundos) antes de disparar o evento Tick. Você chamará o método `Start()` para iniciar o temporizador apenas depois que o jogador escolher o segundo rótulo.  
  
3.  Escolha o ícone do controle de temporizador no Designer de Formulários do Windows e escolha a tecla ENTER, ou clique duas vezes no temporizador, para adicionar um manipulador de eventos **Tick** vazio. Substitua o código pelo código a seguir ou insira-o manualmente no manipulador de eventos.  
  
     [!code-cs[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]  [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]  
  
     O manipulador de eventos Tick realiza três tarefas: primeiro, ele verifica se o temporizador não está em execução chamando o método `Stop()`. Em seguida, ele usa duas variáveis de referência, `firstClicked` e `secondClicked`, para tornar invisíveis novamente os ícones dos dois rótulos que jogador escolheu. Por fim, ele redefine as variáveis de referência `firstClicked` e `secondClicked` para `null` no Visual C# e `Nothing` no Visual Basic. Essa etapa é importante porque é como o programa redefine a si próprio. Agora, ele não está acompanhando nenhum controle `Label` e está pronto para que o jogador escolha um rótulo novamente.  
  
    > [!NOTE]
    >  Um objeto `Timer` tem um método `Start()` que inicia o temporizador e um método `Stop()` que o interrompe. Ao definir a propriedade **Habilitado** do temporizador como **Verdadeiro** na janela **Propriedades**, ele inicia o tique assim que o programa é iniciado. Mas quando você a deixa definida como **Falso**, ele só inicia o tique quando seu método `Start()` é chamado. Normalmente, um temporizador dispara seu evento Tick várias vezes usando a propriedade **Intervalo** para determinar quantos milissegundos deverá aguardar entre os tiques. Você deve ter percebido como o método `Stop()` do temporizador é chamado no evento Tick. Ele coloca o temporizador no *modo monoestável*, o que significa que quando o método `Start()` é chamado, ele aguarda o intervalo especificado, dispara um único evento Tick e é interrompido.  
  
4.  Para ver o novo temporizador em ação, vá para o editor de código e adicione o código a seguir no início e no fim do método do manipulador de eventos `label_Click()`. (Você está adicionando uma instrução `if` no início e três instruções no fim; o restante do método informa o mesmo.)  
  
     [!code-cs[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]  [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]  
  
     O código no início do método verifica se o temporizador foi iniciado verificando o valor da propriedade **Habilitado**. Dessa forma, se o jogador escolher o primeiro e o segundo controle `Label` e o temporizador for iniciado, a escolha de um terceiro rótulo não terá nenhum efeito.  
  
     O código no fim do método define a variável de referência `secondClicked` para acompanhar o segundo controle `Label` que o jogador escolhe e, em seguida, define a cor do ícone desse rótulo como preto, tornando-o visível. Em seguida, ele inicia o temporizador no modo monoestável, de modo que ele aguarda 750 milissegundos e dispara um único evento Tick. O manipulador de eventos Tique do temporizador oculta os dois ícones e redefine as variáveis de referência `firstClicked` e `secondClicked` de modo que o formulário esteja pronto para que o jogador escolha outro par de ícones.  
  
5.  Salve e execute seu programa. Escolha um ícone e ele se tornará visível.  
  
6.  Escolha outro ícone. Ele aparece rapidamente e, em seguida, ambos os ícones desaparecem. Repita isso várias vezes. O formulário agora acompanha o primeiro e o segundo ícone que você escolhe, além de usar o temporizador para pausar antes de fazer os ícones desaparecerem.  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
-   Para ir para a próxima etapa do tutorial, consulte [Etapa 7: Manter os pares visíveis](../ide/step-7-keep-pairs-visible.md).  
  
-   Para retornar à etapa anterior do tutorial, consulte [Etapa 5: Adicionar referências de rótulo](../ide/step-5-add-label-references.md).
