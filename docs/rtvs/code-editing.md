---
title: "Editando código com as Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a198ccc3-5506-48e7-b3b2-9399661b80d5
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 261cced8583b751d74701a8903a10a4584928940
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="editing-r-code-in-visual-studio"></a>Editando código R no Visual Studio
 
As RTVS (Ferramentas do R para Visual Studio) personalizam a experiência de edição do Visual Studio especificamente para R, mantendo todos os recursos e a capacidade de usar extensões. (Por exemplo, se preferir associações de teclas VIM, você poderá instalar a [extensão VsVim](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) gratuita da galeria do Visual Studio.)

Neste tópico:

- [Realce de sintaxe](#syntax-highlighting)
- [Editando e organizando o código](#editing-and-organizing-code)
- [Navegação de código](#code-navigation)
- [Enviando código para a janela interativa](#sending-code-to-the-interactive-window)
- [Formatando o código](#formatting-code)
- [Inserindo comentários Roxygen](#inserting-roxygen-comments)
- [Opções do editor](#editor-options)

Consulte também os tópicos sobre [IntelliSense](code-intellisense.md), [trechos de código](code-snippets.md) e [R Markdown](rmarkdown.md).


## <a name="syntax-highlighting"></a>Realce de sintaxe 

Além de colorir diferentes partes do código, como cadeias de caracteres, comentários e palavras-chave, as RTVS também realçam e habilitam links em comentários:

![Coloração de sintaxe para código R](media/editing-syntax-colors.png)

Para personalizar fontes e determinadas cores de realce, selecione o comando **Ferramentas > Opções**, navegue até **Ambiente > Fontes e Cores** e, em seguida, altere as configurações de itens relacionados ao R na caixa **Exibir itens:**:

![Opções de fontes e cores para código R](media/editing-syntax-colors-options.png)

O Visual Studio também sublinha erros de sintaxe no editor:

![Realce de erro de sintaxe no código R](media/editing-syntax-error.png)

Para alterar esse comportamento, consulte a configuração **Avançado > Verificação de sintaxe** em [opções do editor](#editor-options).

## <a name="editing-and-organizing-code"></a>Editando e organizando o código

Conforme você digita o código, as RTVS fornecem preenchimento automático, conforme descrito na página [IntelliSense](code-intellisense.md). Ele também faz a formatação automática, como o fechamento de chaves e parênteses: 

![Animação de formatação embutida](media/editing-inline-formatting.gif)

Ao digitar chamadas de funções que têm muitos parâmetros, muitas vezes você deseja alinhar os parâmetros para deixar o código mais fácil de ler. As RTVS lembram do recuo que você definiu para os parâmetros e aplica esse recuo automaticamente às linhas subsequentes:

![Animação de recuo automático](media/editing-auto-indentation.gif)

Para alterar esse comportamento, consulte [opções do editor](#editor-options) e veja o grupo **Guias**.

As regiões de código recolhíveis permitem ocultar parte do código temporariamente no editor. O Visual Studio cria várias regiões automaticamente, como nas instruções de várias linhas, a menos que a opção **Avançado > Estrutura de tópicos > Estrutura de tópicos de código** esteja definida como Off.

Para criar uma região sua, coloque o código desejado entre comentários que terminam com `---`. Os controles pequenos +/- à esquerda do código permitem que você expanda e recolha regiões:

![Criando uma região recolhível com comentários](media/editing-collapsible-regions.gif)
 
Por padrão, o Visual Studio insere espaços quando você pressiona a tecla Tab. Novamente você pode alterar esse comportamento, conforme descrito em [Opções, Editor de Texto, Guias](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navegação de código

A navegação de código fornece acesso rápido ao código-fonte do seu programa do R e de suas bibliotecas. Esses recursos mantêm você no fluxo do seu trabalho em vez de precisar pesquisar manualmente o código.

**Ir para definição** rapidamente salta para uma definição de função ou um minieditor pop-up embutido para ler o código-fonte de uma função de biblioteca. Basta clicar com o botão direito do mouse na função de interesse e selecionar **Ir para Definição** ou colocar o cursor na função e pressionar F12.

Este comando abre uma nova janela do editor que contém o código-fonte para a função. O cursor é convenientemente posicionado no início da definição de função.

**Definição de espiada**, invocado do menu acionado com um clique do botão direito do mouse ou com Alt + F12, insere uma região rolável e somente leitura que contém o código-fonte da função abaixo da chamada de função:

![Animação para definição de espiada](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Enviando o código para a janela interativa

Muitos desenvolvedores gostam escrever código no editor e, em seguida, enviá-lo para a [janela interativa](interactive-repl.md) para teste imediato [também conhecido como REPL (Read-Evaluate-Print-Loop)]. Pressionar Ctrl+Enter no editor de R envia a linha de código atual para a janela interativa e, em seguida, coloca o cursor na próxima linha. Com Ctrl + Enter, você pode percorrer seu código efetivamente no editor.

Você também pode selecionar o código e pressionar Ctrl + Enter para aplicar essa seleção inteira. Como alternativa, clique com o botão direito do mouse na seleção e selecione **Executar em Interativo**.

## <a name="formatting-code"></a>Formatando o código

A formatação automática do Visual Studio mantém o código que você escreve, bem como o código que você cola no editor, formatados conforme definido por suas preferências. Você também pode fazer uma seleção, clicar com o botão direito do mouse e selecionar **Formatar Seleção** (Ctrl + K, F) para aplicar essas preferências. Por exemplo, se você tiver uma definição de função inteira em uma única linha:

```R
f<-function  (a){  return(a + 1) }
```

A aplicação da formatação a limpará deixando assim:

```R
f <- function(a) { return(a + 1) }
```

Para reformatar o arquivo de código inteiro, selecione **Editar > Avançado > Formatar Documento** (Ctrl + E, D).

A formatação automática é uma operação separada que pode ser desfeita. Por exemplo, se você colar o código no editor e a formatação for aplicada, selecionar **Editar > Desfazer** ou pressionar Ctrl+Z uma vez reverterá a formatação, um segundo Desfazer desfaz a ação de colar em si.
 
As opções de formatação (incluindo a desativação de formatação) são definidas por meio de **Ferramentas > Opções** na guia **Editor de Texto > R > Avançado**. Você pode ir diretamente para essa página usando o comando **Ferramentas do R > Opções do editor...** ou clicando com o botão direito do mouse no editor e selecionando **Opções de formatação...**. Consulte a seção de [opções do editor](#editor-options) para obter detalhes.
 
## <a name="inserting-roxygen-comments"></a>Inserindo comentários Roxygen

As RTVS fornecem um atalho para a geração de comentários [Roxygen](http://roxygen.org/) usando os nomes de parâmetro de uma função. Basta digitar `###` em uma linha em branco acima da definição de função:

![Animação da inserção de um comentário Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opções do editor

As oOpções específicas do editor são definidas por meio do comando **Ferramentas > Opções**, navegando até **Editor de Texto > R** ou usando o comando de atalho **Ferramentas do R > Opções do Editor...**.

As opções nas guias **Geral**, **Barras de rolagem** e **Guias** não são específicas para R, mas são configurações gerais do Visual Studio disponíveis para todas as linguagens, mas são aplicadas de acordo com cada linguagem. Para obter detalhes, consulte os seguintes tópicos:

- [Opções, Editor de Texto, Todas as Linguagens](../ide/reference/options-text-editor-all-languages.md)
- [Rastrear o código personalizando a barra de rolagem](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opções, editor de texto, guias](../ide/reference/options-text-editor-all-languages-tabs.md)

As opções na guia **R > Avançado** guia são específicas para RTVS:

| Grupo | Opção | Padrão | Descrição |
| --- | --- | --- | --- |
| Formatação | Formatação automática | On | Reformata o código enquanto você digita. Não afeta os comandos **Formatar Seleção** ou **Formatar Documento**. |
| | Chaves expandidas | Off | Coloca uma { aberta em uma nova linha. |
| | Formatar ao colar | On | Aplica a formatação ao colar. |
| | Formatar escopo em } | On | Formata o escopo depois de digitar uma } de fechamento. |
| | Espaço após a vírgula | On | Coloca um espaço depois de vírgulas. |
| | Espaço após a palavra-chave | On | Coloca um espaço depois de palavras-chave como `if`, `while` e `repeat`. |
| | Espaço antes de { | On | Coloca um espaço antes de uma { de abertura. |
| | Espaços antes e depois de = | On | Insere espaços antes e depois de um sinal de igual. |
| IntelliSense | Confirmar com a tecla Enter | Off | Confirma a seleção de preenchimento automático quando Enter é pressionada. |
| | Confirmar com a tecla Espaço | Off | Confirma a seleção de preenchimento automático quando Espaço é pressionada.|
| | Lista de conclusão no primeiro caractere | On | Mostra a lista de conclusão nos primeiros tipos de caracteres. Quando Off, uma lista de conclusão é exibida com **Editar > IntelliSense > Listar Membros** (Ctrl + J). |
| | Lista de conclusão com a tecla Tab | Off | Invoca a lista de conclusão ao digitar um ou mais caracteres e pressionar a tecla Tab. |
| | Corresponder parcialmente ao digitar nomes de argumento | Off | Ao digitar os nomes de argumento em uma chamada de função, a ajuda de assinatura mostra uma descrição do argumento que é a melhor correspondência. |
| Janela Interativa | Verificação de sintaxe no console do R | Off | Aplica a verificação na janela interativa de sintaxe. A verificação de sintaxe pode não funcionar corretamente com instruções de várias linhas. | 
| Estrutura de tópicos | Estrutura de tópicos de código | On | Cria regiões recolhíveis automaticamente para áreas como instruções de várias linhas. | 
| Verificação de sintaxe | Mostrar erros de sintaxe | On | Habilita a verificação de sintaxe automática do código. |

