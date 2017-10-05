---
title: "Introdução ao R no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 39228cf0-8d21-43bb-a2ce-5e5fdc81ec41
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b9fb38bf7e21924d7fbece72978e99d298a42b74
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="getting-started-with-r-tools-for-visual-studio"></a>Introdução às Ferramentas do R para Visual Studio

Depois de instalar as RTVS (Ferramentas do R para Visual Studio) (consulte [Instalação](installation.md)), você poderá ter uma rápida ideia da experiência que essas ferramentas fornecem. As seções a seguir guiam você em um pequeno tour:

- [Criar um projeto R](#create-an-r-project)
- [Explorar a janela interativa e o IntelliSense](#explore-the-interactive-window-and-intellisense)
- [Experimentar recursos de edição de código](#experience-code-editing-features)
- [Depurando seu código](#debugging-your-code)
- [Próximas etapas](#next-steps)

## <a name="create-an-r-project"></a>Criar um projeto R

1. Inicie o Visual Studio.
1. Escolha **Arquivo > Novo > Projeto...** (Ctrl + Shift + N)
1. Selecione "Projeto R" em **Modelos > R**, dê ao projeto um nome e um local e selecione **OK**:

   ![Caixa de diálogo Novo Projeto para R no Visual Studio (RTVS no VS2017)](media/getting-started-01-new-project.png)

1. Quando o projeto for criado, você verá as seguintes janelas:

    - À direita está o Gerenciador de Soluções do Visual Studio, em que você vê seu projeto contido dentro de uma *solução*. (As soluções podem conter qualquer número de projetos de diferentes tipos, consulte [Projetos](projects.md) para obter detalhes.
    - No canto superior esquerdo estará um novo arquivo R (`script.R`) em que você poderá editar o código-fonte com todos os recursos de edição do Visual Studio.
    - No canto inferior esquerdo estará a janela **R Interativo** na qual você pode desenvolver e testar o código de forma interativa.

> [!Note]
> Você pode usar a janela **R Interativo** sem abrir nenhum projeto e até mesmo quando um tipo de projeto diferente é carregado. Basta selecionar **Ferramentas do R > Janelas > R Interativo** a qualquer momento.

## <a name="explore-the-interactive-window-and-intellisense"></a>Explorar a janela interativa e o IntelliSense

1. Teste se a janela interativa está funcionando digitando `3 + 4` e pressionando Enter para ver o resultado:

    ![Janela R Interativo no Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Insira algo um pouco mais complicado, `ds <- c(1.5, 6.7, 8.9) * 1:12` e, em seguida, insira `ds` para ver o resultado:

    ![Exemplo interativo adicional do R no Visual Studio](media/getting-started-03-interactive2.png)

1. Digite `mean(ds)`, mas observe que assim que você digitar `m` ou `me`, o Visual Studio IntelliSense fornecerá opções de preenchimento automático. Quando o preenchimento que você deseja for selecionado na lista, pressione a tecla Tab para inseri-lo. Você pode alterar a seleção usando o mouse ou as teclas de direção.

    ![O IntelliSense que aparece quando você insere código](media/getting-started-04-intellisense1.png)

1. Depois de preencher `mean`, digite o parêntese de abertura `(` e observe como o IntelliSense fornece ajuda embutida para a função:

    ![IntelliSense mostrando ajuda para uma função](media/getting-started-05-intellisense2.png)

1. Preencha a linha `mean(ds)` e pressione Enter para ver o resultado (`[1] 39.51667`).

1. A janela interativa é integrada à ajuda, portanto, inserir `?mean` exibe a ajuda para essa função na janela **Ajuda do R** no Visual Studio. Para obter detalhes, consulte [Ajuda nas Ferramentas do R para Visual Studio](getting-started-help.md).

    ![Janela Ajuda do R no Visual Studio](media/getting-started-06-help.png)

1. Alguns comandos, como `plot(1:100)`, abrem uma nova janela no Visual Studio quando a saída não pode ser exibida diretamente na janela interativa:

    ![Exibição de um gráfico no Visual Studio](media/getting-started-07-plot-window.png)

A janela interativa também permite que você examine seu histórico, carregue e salve espaços de trabalho, anexe a um depurador e interaja com os arquivos de código-fonte em vez de usar os recursos de copiar e colar. Consulte [Trabalhando com a janela do R Interativo](interactive-repl.md) para obter detalhes.

## <a name="experience-code-editing-features"></a>Experimentar recursos de edição de código

O rápido trabalho com a janela interativa demonstra recursos de edição básicos como o IntelliSense que também funcionam no editor de código. Se inserir o mesmo código que antes, você verá os mesmos prompts de preenchimento automático e do IntelliSense, mas não a saída.

Escrever código em um arquivo `.R` permite que você veja todo o código de uma vez e torna mais fácil fazer pequenas alterações e, em seguida, ver o resultado rapidamente executando o código na janela interativa. Você também pode ter quantos arquivos desejar em um projeto. Quando o código está em um arquivo, você também pode executá-lo passo a passo no depurador (discutido posteriormente neste tópico). Esses recursos são muito úteis para desenvolver algoritmos computacionais e escrever código para manipular um ou mais conjuntos de dados, principalmente quando se deseja examinar todos os resultados intermediários.

Por exemplo, as seguintes etapas criam um pequeno código para explorar o [Teorema central do limite](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipédia). [Este exemplo é adaptado do *Cookbook do R* (Guia do R) de Paul Teetor.]

1. No editor `script.R`, digite o seguinte código:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Para ver os resultados rapidamente, selecione todo o código (Ctrl + A), pressione Ctrl + Enter ou clique com botão direito do mouse e selecione **Executar em Interativo**. Todo o código selecionado é executado na janela interativa como se você o digitasse diretamente em uma janela de gráficos:

    ![Exibição de um gráfico no Visual Studio](media/getting-started-08-plot1.png)

1. Para uma única linha, basta pressionar Ctrl+Enter a qualquer momento para executar essa linha na janela interativa.

> [!Tip]
> Aprenda o padrão de fazer edições e pressionar Ctrl + Enter (ou selecionar tudo com Ctrl + A e, em seguida, pressionar Ctrl + Enter) para executar o código rapidamente. Fazer isso é muito mais eficiente do que usar o mouse para as mesmas operações.
> 
> Além disso, você pode arrastar e soltar a janela de gráficos para fora do quadro do Visual Studio e colocá-la em qualquer lugar da tela que desejar. Você pode redimensionar a janela de gráficos para as dimensões desejadas e salve-a em uma imagem ou arquivo PDF.

1. Adicione algumas outras linhas de código para incluir um segundo gráfico:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))    
    lines(density(samp.means))
    ```

1. Pressione Ctrl+A e Ctrl+Enter novamente para executar o código, produzindo o seguinte resultado:

    ![Gráfico dual atualizado no Visual Studio](media/getting-started-09-plot2.png)

1. O problema é que o primeiro gráfico determina a escala vertical, portanto, o segundo gráfico (com `lines`) não se encaixa. Para corrigir esse problema, precisamos definir o parâmetro `ylim` na chamada `plot`, mas para fazer isso corretamente, precisamos adicionar código para calcular o valor máximo da vertical. Fazer isso linha por linha na janela interativa é inconveniente porque é preciso reorganizar o código para usar `samp.means` antes de chamar `plot`. No entanto, em um arquivo de código, podemos fazer as edições apropriadas com facilidade:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. CTRL + A e Ctrl + Enter novamente para ver o resultado:

    ![Gráfico dual atualizado no Visual Studio com a escala ajustada corretamente](media/getting-started-10-plot3.png)

Há mais coisas que você pode fazer no editor. Para obter detalhes, consulte [editando código](code-editing.md), [IntelliSense](code-intellisense.md) e [trechos de código](code-snippets.md).

## <a name="debugging-your-code"></a>Depurando seu código

Uma das principais vantagens do Visual Studio é sua interface do usuário de depuração. As RTVS são criadas sobre essa base sólida e adicionam uma interface do usuário inovadora como o [Gerenciador de Variáveis e o Visualizador da Tabela de Dados](variable-explorer.md). Aqui, vamos apenas dar uma primeira olhada na depuração.

1. Para começar, redefina o espaço de trabalho atual para Limpar tudo o que fizemos até agora, usando o comando de menu **Ferramentas do R > Sessão > Redefinir**. Por padrão, tudo o que você faz na janela interativa é acumulado para a sessão atual, que também será usado pelo depurador. Ao redefinir a sessão, você garante que a sessão de depuração seja iniciada sem nenhum dado preexistente. O comando **Redefinir**, no entanto, não afeta seu arquivo de origem `script.R`, pois ele é gerenciado e salvo fora do espaço de trabalho.

1. Com o arquivo `script.R` criado na seção anterior, defina um ponto de interrupção na linha que começa com `pop <-` colocando o cursor nessa linha e, em seguida, pressionando F9 ou selecionando o comando de menu **Depurar > Alternar Ponto de Interrupção**. De forma alternativa, apenas clique na margem esquerda (ou medianiz) dessa linha em que o ponto de interrupção vermelho aparece:

    ![Definindo um ponto de interrupção no editor](media/getting-started-11-debug1.png)

1. Inicie o depurador com o código em `script.R` selecionando o botão **Arquivo de inicialização de origem** na barra de ferramentas, selecionando os itens de menu **Depurar > Arquivo de inicialização de origem** ou pressionando F5. O Visual Studio entra em seu modo de depuração e inicia a execução do código. No entanto, a execução é interrompida na linha em que você definiu o ponto de interrupção:

    ![Parando em um ponto de interrupção no depurador do Visual Studio](media/getting-started-12-debug2.png)

1. Durante a depuração, o Visual Studio fornece a capacidade de depurar seu código linha por linha. Você também pode intervir nas funções, passar por elas ou sair delas para o contexto de chamada. Esses recursos, juntamente com outros, podem ser encontrados no menu **Depurar**, o menu de contexto acionado com um clique do botão direito do mouse no editor e na barra de ferramentas Depuração:

    ![Barra de ferramentas de depuração no Visual Studio](media/getting-started-13-debug3.png)

1. Ao interromper no ponto de interrupção, você pode examinar os valores das variáveis. Localize a janela **Autos** no Visual Studio e selecione a guia na parte inferior chamada **Locais**. A janela **Locais** mostra as variáveis locais no ponto atual no programa. Se você tiver parado no ponto de interrupção definido anteriormente, verá que a variável `pop` ainda não está definido. Agora, use o comando **Depurar > Depuração Parcial** (F10) e você verá o valor de `pop` aparecer:

    ![Janela Locais no Visual Studio](media/getting-started-14-debug4.png)

1. Para examinar variáveis em escopos diferentes, incluindo o escopo global e os escopos de pacote, use o [Gerenciador de Variáveis](variable-explorer.md). O Gerenciador de Variáveis também oferece a capacidade de mudar para um modo de exibição de tabela com colunas classificáveis e exportar dados para um arquivo CSV.

    ![Exibição expandida do Gerenciador de Variáveis](media/variable-explorer-expanded-results.png)

1. Você pode continuar percorrendo o programa linha por linha ou selecionar **Continuar** (F5) para executá-lo até a conclusão (ou o até o próximo ponto de interrupção).

Para aprofundar-se, consulte [Depuração](debugging.md) e [Gerenciador de Variáveis](variable-explorer.md).

## <a name="next-steps"></a>Próximas etapas

Neste passo a passo, você aprendeu as noções básicos de projetos R, usando a janela interativa, edição de código e depuração no Visual Studio. Para continuar a explorar mais recursos, consulte os tópicos a seguir, bem como os tópicos mostrados no índice:

- [Projetos de exemplo](getting-started-samples.md)
- [Editando código](code-editing.md)
- [Depuração](debugging.md)
- [Espaços de trabalho](workspaces.md)
- [Visualizando dados](visualizing-data.md)

