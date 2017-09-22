---
title: "Tutorial 2: criar um teste de matemática temporizado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 17
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8be8666b38d4c63834ae2cc8869cb7a4e4cbd43e
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutorial 2: Criar um teste de matemática com cronômetro
Neste tutorial, você cria um teste no qual o tomador de teste deve responder a quatro problemas aritméticos aleatórios dentro de um tempo especificado. Você aprenderá como:  
  
-   Gere números aleatórios usando a classe de `Random`.  
  
-   Disparar eventos para que ocorram em um horário específico usando um controle de **Temporizador**.  
  
-   Fluxo do programa de controle usando instruções de `if else`.  
  
-   Execute operações aritméticas básicas no código.  
  
 Quando você terminar, seu teste ficará parecido com a imagem a seguir, mas com números diferentes.  
  
 ![Teste de matemática com quatro problemas](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Teste que você cria neste tutorial  
  
 Para baixar uma versão concluída do teste, consulte [Exemplo de tutorial de teste completo de matemática](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
>  O Visual C# e o Visual Basic são abordados neste tutorial, por isso, concentre-se nas informações específicas da linguagem de programação que você está usando.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Etapa 1: criar um projeto e adicionar rótulos ao formulário](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Comece criando o projeto, alterando propriedades e adicionando controles `Label`.|  
|[Etapa 2: criar um problema de adição aleatório](../ide/step-2-create-a-random-addition-problem.md)|Crie um problema de adição, e use a classe de `Random` para gerar números aleatórios.|  
|[Etapa 3: adicionar um temporizador de contagem regressiva](../ide/step-3-add-a-countdown-timer.md)|Adicione um timer de contagem regressiva de modo que o teste possa ser cronometrado.|  
|[Etapa 4: adicionar o método CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Adicione um método para verificar se o comprador de teste inseriu uma resposta correta para o problema.|  
|[Etapa 5: adicionar manipuladores de eventos Enter para os controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Adicione manipuladores de eventos que facilitam a tomada do teste.|  
|[Etapa 6: adicionar um problema de subtração](../ide/step-6-add-a-subtraction-problem.md)|Adicione um problema de subtração que gerencia números aleatórios, usa o timer, e o verifica se as respostas estão corretas.|  
|[Etapa 7: adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md)|Adicione problemas de divisão e multiplicação que geram números aleatórios, usam o timer, e verificam se as respostas estão corretas.|  
|[Etapa 8: personalizar o teste](../ide/step-8-customize-the-quiz.md)|Tente outros recursos, como alterar cores e adicionar uma dica.|
