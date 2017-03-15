---
title: "Etapa 8: adicionar um método para verificar se o jogador ganhou | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 17
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 88c199781019e884673222500b44a3afc69b3af8
ms.lasthandoff: 02/22/2017

---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Etapa 8: Adicionar um método para verificar se o jogador ganhou
Você criou um jogo divertido, mas ele precisa de um item adicional para ser finalizado. O jogo deve terminar quando os jogadores ganham, de modo que você precisa adicionar um método `CheckForWinner()` para verificar se o jogador ganhou.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Para adicionar um método para verificar se o jogador ganhou  
  
1.  Adicione um método `CheckForWinner()` ao fim do seu código, abaixo do manipulador de eventos `timer1_Tick()`, conforme mostrado no código a seguir.  
  
     [!code-cs[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]  
  
     O método usa outro loop `foreach` no Visual C# ou o loop `For Each` no Visual Basic para passar em cada rótulo no TableLayoutPanel. Ele usa o operador de igualdade (`==` no Visual C# e `=` no Visual Basic) para examinar a cor do ícone de cada rótulo e verificar se ela corresponde ao plano de fundo. Se as cores corresponderem, o ícone permanecerá invisível e o jogador não combinou todos os ícones restantes. Nesse caso, o programa usa uma instrução `return` para ignorar o restante do método. Se o loop passar por todos os rótulos sem executar a instrução `return`, isso significa que todos os ícones no formulário foram combinados. O programa mostra uma MessageBox para parabenizar o jogador ganhador e, em seguida, chama o método `Close()` do formulário para encerrar o jogo.  
  
2.  Em seguida, o manipulador de eventos Click do rótulo chama o novo método `CheckForWinner()`. Verifique se seu programa busca um ganhador imediatamente depois que ele mostra o segundo ícone que o jogador escolhe. Procure a linha onde você define a cor do segundo ícone escolhido e chame o método `CheckForWinner()` logo depois disso, conforme mostrado no código a seguir.  
  
     [!code-cs[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]  
  
3.  Salve e execute o programa. Jogue o jogo e combine todos os ícones. Quando você ganha, o programa exibe uma MessageBox de congratulação (conforme mostrado na imagem a seguir) e fecha a caixa.  
  
     ![Jogo da memória com MessageBox](../ide/media/express_tut4step8.png "Express_Tut4Step8")  
Jogo da memória com MessageBox  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
-   Para acessar a próxima etapa do tutorial, consulte [Etapa 9: Experimentar outros recursos](../ide/step-9-try-other-features.md).  
  
-   Para retornar à etapa anterior do tutorial, consulte [Etapa 7: Manter os pares visíveis](../ide/step-7-keep-pairs-visible.md).
