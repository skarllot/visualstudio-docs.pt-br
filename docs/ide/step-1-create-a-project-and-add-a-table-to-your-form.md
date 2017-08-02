---
title: "Etapa 1: criar um projeto e adicionar uma tabela ao formulário | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 19
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
ms.openlocfilehash: a112e67966ddf76e6bde53153828c72dbf5b478b
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Etapa 1: Criar um projeto e adicionar uma tabela ao formulário
A primeira etapa da criação de um jogo da memória é criar o projeto e adicionar uma tabela ao formulário. A tabela ajuda a alinhar os ícones em uma grade 4x4 de forma ordenada. Você também define várias propriedades para aprimorar a aparência do tabuleiro do jogo.  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Para criar um projeto e adicionar uma tabela ao formulário  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Se não estiver usando o Visual Studio Express, primeiramente, você precisará selecionar uma linguagem de programação. Na lista **Modelos Instalados**, escolha **Visual C#** ou **Visual Basic**.  
  
3.  Na lista de modelos de projeto, escolha **Aplicativo do Windows Forms**, dê o nome **MatchingGame** ao projeto e escolha o botão **OK**.  
  
4.  Na janela **Propriedades**, defina as propriedades de formulário a seguir.  
  
    1.  Altere a propriedade **Texto** do formulário, de **Form1** para **Jogo da Memória**. Esse texto aparece na parte superior da janela do jogo.  
  
    2.  Defina o tamanho do formulário para 550 pixels de largura por 550 de altura. Você pode fazer isso definindo a propriedade **Tamanho** como **550, 550** ou arrastando o canto do formulário até visualizar o tamanho correto no canto inferior direito do IDE (ambiente de desenvolvimento integrado).  
  
5.  Exiba a caixa de ferramentas escolhendo a guia **Caixa de Ferramentas** no lado esquerdo do IDE.  
  
6.  Arraste um controle `TableLayoutPanel` da categoria **Contêineres** na caixa de ferramentas e, em seguida, defina as propriedades a seguir para ele.  
  
    1.  Defina a propriedade **BackColor** como **CornflowerBlue**. Para isso, abra a caixa de diálogo **BackColor** escolhendo a seta suspensa próxima à propriedade **BackColor** na janela **Propriedades**.  Em seguida, escolha a guia **Web** na caixa de diálogo **BackColor** para exibir uma lista de nomes de cores disponíveis.  
  
        > [!NOTE]
        >  As cores não estão em ordem alfabética e CornflowerBlue está quase no fim da lista.  
  
    2.  Defina a propriedade **Encaixar** como **Preenchimento** escolhendo o botão suspenso próximo à propriedade e escolhendo o botão grande do meio. Isso estende a tabela para que ela cubra o formulário inteiro.  
  
    3.  Defina a propriedade **CellBorderStyle** como **Baixo-relevo**. Isso fornece bordas visuais entre cada célula no tabuleiro.  
  
    4.  Escolha o botão triangular no canto superior direito do TableLayoutPanel para exibir o menu de tarefas.  
  
    5.  No menu de tarefas, escolha **Adicionar Linha** duas vezes para adicionar mais duas linhas e escolha **Adicionar Coluna** duas vezes para adicionar mais duas colunas.  
  
    6.  No menu de tarefas, escolha **Editar Linhas e Colunas** para abrir a janela **Estilos de Coluna e Linha**. Escolha cada uma das colunas, escolha o botão de opção **Porcentagem** e defina a largura de cada coluna como 25% da largura total. Em seguida, selecione **Linhas** na caixa suspensa na parte superior da janela e defina a altura de cada linha como 25%. Quando tiver terminado, escolha o botão **OK**.  
  
     O TableLayoutPanel agora deve ser uma grade 4x4, com dezesseis células quadradas de igual tamanho. Essas linhas e colunas estão onde as imagens do ícone aparecerão mais tarde.  
  
7.  Certifique-se de que TableLayoutPanel esteja selecionado no editor de formulários. Para confirmar isso, você deve ver **tableLayoutPanel1** na parte superior da janela **Propriedades**. Se não estiver selecionado, escolha TableLayoutPanel no formulário ou escolha-o no controle suspenso na parte superior da janela **Propriedades**.  
  
     Enquanto TableLayoutPanel estiver selecionado, abra a caixa de ferramentas e adicione um controle **Rótulo** (localizado na categoria **Controles Comuns**) à célula superior esquerda de TableLayoutPanel. O controle `Label` agora deve estar selecionado no IDE. Defina as propriedades a seguir para ele.  
  
    1.  Verifique se a propriedade **BackColor** do rótulo está definida como **CornflowerBlue**.  
  
    2.  Defina a propriedade **AutoSize** para **False**.  
  
    3.  Defina a propriedade **Encaixar** como **Preenchimento**.  
  
    4.  Defina a propriedade **TextAlign** como **MiddleCenter** escolhendo o botão suspenso próximo à propriedade e escolhendo o botão do meio. Isso garante que o ícone apareça no meio da célula.  
  
    5.  Escolha a propriedade **Fonte**. O botão reticências (…) deverá aparecer.  
  
    6.  Escolha o botão de reticências e defina o valor de **Fonte** como **Webdings**, o **Estilo da Fonte** como **Negrito** e o **Tamanho** para **72**.  
  
    7.  Defina a propriedade **Texto** do rótulo como a letra **c**.  
  
         A célula superior esquerda no TableLayoutPanel agora deve conter uma caixa preta centrada em um plano de fundo azul.  
  
        > [!NOTE]
        >  A fonte Webdings é uma fonte de ícones que acompanha o sistema operacional Windows. No seu jogo da memória, o jogador precisa encontrar pares de ícones, de modo que você usa essa fonte para exibir os ícones a serem encontrados. Em vez de colocar **c** na propriedade **Texto**, tente inserir diferentes letras para ver quais ícones são exibidos. Um ponto de exclamação é uma aranha, um N maiúsculo é um olho e uma vírgula é uma pimenta.  
  
8.  Escolha o controle de rótulo e copie-o ao lado da célula no TableLayoutPanel. (Escolha as teclas Ctrl+C ou, na barra de menus, escolha **Editar**, **Copiar**.) Cole-o. (Escolha as teclas Ctrl+V ou, na barra de menus, escolha **Editar**, **Colar**.) Uma cópia do primeiro rótulo aparece na segunda célula de TableLayoutPanel. Cole-o novamente e outro rótulo aparecerá na terceira célula. Continue colando controles `Label` até que todas as células sejam preenchidas.  
  
    > [!NOTE]
    >  Se você colar muitas vezes, o IDE adicionará uma nova linha ao TableLayoutPanel para que ele tenha um local para adicionar seu novo controle de rótulo. Isso pode ser desfeito. Para remover a nova célula, escolha as teclas Ctrl+Z ou, na barra de menus, escolha **Editar**, **Desfazer**.  
  
     Agora seu formulário é apresentado. Ele deve se parecer com a imagem a seguir.  
  
     ![Formulário inicial do jogo da memória](~/ide/media/express_tut4step1.png "Express_Tut4Step1")  
Formulário inicial do jogo da memória  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
-   Para ir para a próxima etapa do tutorial, consulte [Etapa 2: adicionar um objeto aleatório e uma lista de ícones](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   Para retornar ao tópico de visão geral, consulte [Tutorial 3: criar um jogo da memória](../ide/tutorial-3-create-a-matching-game.md).
