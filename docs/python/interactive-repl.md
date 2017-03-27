---
title: REPL interativo do Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: f31d92f193af3fb32f61030ca52e444ae2baa60b
ms.lasthandoff: 03/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>Trabalhando com a Janela Interativa do Python

O Visual Studio fornece uma janela interativa REPL (leitura-avaliação-impressão-loop) para cada um dos ambientes do Python, que é uma melhoria do REPL obtido com `python.exe` na linha de comando. A janela interativa (aberta com os comandos de menu **Exibir > Outras Janelas > &lt;ambiente&gt; Interativo**) permite inserir um código arbitrário do Python e ver resultados imediatos, o que ajuda você a aprender e experimentar com APIs e a desenvolver o código de trabalho de forma interativa a ser incluído em seus projetos.

![Janela interativa do Python](media/interactive-window.png)

O Visual Studio tem diversos modos REPL do Python à sua disposição:

| REPL | Descrição | Edição | Depuração | Imagens |
| --- | --- | --- | --- | --- |
| Padrão | REPL padrão, que se comunica com o Python diretamente | Edição padrão (várias linhas, etc.). | Sim, por meio de `$attach` | Não |
| Depurar | REPL padrão, que se comunica com o processo depurado do Python | Edição padrão | Somente depuração | Não |
| IPython | O REPL se comunica com o back-end do IPython | Comandos do IPython, funcionalidades do Pylab | Não | Sim, embutido no REPL |
| IPython sem Pylab | O REPL se comunica com o back-end do IPython | IPython padrão | Não | Sim, em uma janela separada | 

Este tópico descreve os modos REPL **Padrão** e **Depuração**. Para obter detalhes sobre os modos do IPython, consulte [Usando o REPL do IPython](interactive-repl-ipython.md).

Para obter uma introdução à Janela interativa do Python, assista a [Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introdução ao Python no Visual Studio, parte 5: REPL interativo) (youtube.com, 2min51s).

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>Abrindo uma janela interativa

Há várias maneiras para abrir a janela interativa de um ambiente.

Primeiro, mude para a janela Ambientes do Python (**Exibir > Outras Janelas > Ambientes do Python** ou Ctrl-K, Ctrl-`) e selecione o comando ou botão **Abrir Janela Interativa** de um ambiente escolhido.

![Link Janela Interativa na janela Ambientes do Python](media/interactive-window-opening.png)

Em segundo lugar, **Exibir > Outras Janelas** contém comandos **Interativos** para cada um dos ambientes, geralmente, mostrados próximo à parte inferior do menu:

![Itens de menu da Janela Interativa em Exibir > Outras Janelas](media/interactive-window-menu.png)

Em terceiro lugar, é possível abrir uma janela interativa no arquivo de inicialização do projeto ou para um arquivo independente, selecionando o comando de menu **Depurar > Executar [Projeto | Arquivo] em Python Interativo** (Shift+Alt+F5):

![Executar Projeto no menu Python Interativo](media/interactive-execute-project.png)

Por fim, é possível selecionar o código no arquivo e usar o comando [Enviar código para interativa](#send-code-to-interactive) descrito abaixo.

## <a name="interactive-window-options"></a>Opções da janela interativa

É possível controlar vários aspectos da janela interativa por meio da opção **Configurar janela interativa** na janela Ambientes do Python ou por meio de **Ferramentas > Opções > Ferramentas Python > Janelas Interativas**:

![Opções da janela interativa do Python](media/interactive-window-options.png)

Observe que também há um conjunto separado de opções para a opção **Janela Interativa de Depuração**, que controla o comportamento durante o uso em uma sessão de depuração:

![Opções de depuração da janela interativa do Python](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>Usando a janela interativa

Depois de abrir a janela interativa, é possível começar a inserir o código linha por linha no prompt `>>>`. A janela interativa executa cada linha conforme ela é inserida, o que inclui a importação de módulos, definição de variáveis e assim por diante. É possível ver isso nas duas primeiras linhas mostradas no gráfico abaixo:

![Janela interativa do Python](media/interactive-window.png)

A exceção é quando uma instrução termina em dois-pontos, assim como ocorre com a instrução `for` acima, pois a janela interativa sabe que precisa de linhas de código adicionais antes de executar o bloco de código corretamente. Nesse caso, o prompt de linha muda para `...`, indicando que é necessário inserir linhas adicionais no bloco, conforme mostrado na quarta e quinta linhas do gráfico acima. Ao pressionar Enter em uma linha em branco, a janela interativa fecha o bloco e o executa no interpretador.

> [!Tip]
> A janela interativa é uma melhoria da experiência comum do REPL de linha de comando do Python, recuando automaticamente as instruções que pertencem a um escopo ao redor. Seu histórico (recuperado com a seta para cima) também fornece itens de várias linhas, enquanto o REPL de linha de comando fornece somente linhas individuais.

A janela interativa é uma ótima maneira de experimentar uma nova biblioteca. Você pode importar a biblioteca, inspecionar subpacotes, classes e funções.  O Python pode fornecer todas essas informações por meio de sua função `help()`.  Além disso, o suporte do Python no Visual Studio fornece sugestões e documentação com base na modelagem de código usada no editor, o que é feito sem a necessidade de executar a biblioteca.  Ao executar o código, o Visual Studio usa as informações do tempo de execução do Python para melhorar essas sugestões.  

<a name="meta-commands"></a> A janela interativa também dá suporte a vários metacomandos. Todos os metacomandos começam com `$` e é possível digitar `$help` para obter uma lista dos metacomandos e `$help <command>` para obter detalhes de uso de um comando específico.

| Metacomando | Descrição |
| --- | --- |
| `$$` | Insere um comentário, que é útil para comentar o código ao longo da sessão. |
| `$attach` | Anexa o depurador do Visual Studio ao processo da janela REPL para habilitar a depuração. |
| `$cls`, `$clear` | Limpa o conteúdo da janela do editor, deixando intactos o histórico e o contexto de execução. |
| `$help` | Exibe uma lista de comandos ou a ajuda sobre um comando específico. |
| `$load` | Carrega comandos do arquivo e os executa até a conclusão. |
| `$mod` | Muda o escopo atual para o nome de módulo especificado. |
| `$reset` | Redefine o ambiente de execução com o estado inicial, mas mantém o histórico. |
| `$wait` | Aguarda, pelo menos, o número especificado de milissegundos. |

Os comandos também são extensíveis por meio do MEF (o Managed Extensibility Framework para .NET).

## <a name="switching-scopes"></a>Mudando escopos

Por padrão, a janela interativa de um projeto tem como escopo o arquivo de inicialização do projeto, como se ele fosse executado no prompt de comando. Para um arquivo independente, ele tem como escopo esse arquivo. No entanto, a qualquer momento, o menu suspenso na parte superior da janela interativa permite alterar o escopo durante a sessão de REPL:

![Escopos da janela interativa](media/interactive-scopes.png)

Ao importar um módulo, como digitar `import os`, você verá opções na lista suspensa para mudar para um escopo nesse módulo. Você também verá uma mensagem na janela interativa indicando o novo escopo; portanto, é possível acompanhar como você chegou a determinado estado durante a sessão.

A inserção de `dir()` em um escopo exibe os identificadores válidos no escopo, incluindo nomes de função, classes e variáveis. Por exemplo, o uso de `$mod importlib` seguido por `dir()` mostra o seguinte:

![Janela interativa no escopo de importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>Comando Enviar código para interativa

Além de trabalhar na janela interativa diretamente, é possível selecionar o código no editor, clicar com o botão direito do mouse e escolher **Enviar para interativa**:

![Comando de menu Enviar para interativa](media/interactive-send-to.png)

Isso é útil para o desenvolvimento de código iterativo ou evolucionário, incluindo o teste do código durante o desenvolvimento. Por exemplo, depois de enviar um trecho de código para a janela interativa e ver sua saída, é possível pressionar a seta para cima para exibir o código novamente, modificá-lo e testá-lo rapidamente pressionando Ctrl+Enter. (Pressionar Enter no final da entrada o executa, mas pressionar Enter no meio da entrada insere uma nova linha.) Depois de obter o código desejado, é possível copiá-lo novamente com facilidade para o arquivo de projeto.

Também é possível selecionar o código, clicar com o botão direito do mouse e selecionar **Enviar para Módulo de Definição**, que pesquisa o processo interativo para encontrar o módulo que corresponde ao arquivo atual que está sendo editado. Se o comando encontrar o módulo correto, ele usará o metacomando `$mod` para mudar para esse módulo (que se tornará parte do histórico de sessão da janela interativa) e colará a seleção na janela interativa para avaliação. Isso fornece um atalho para o processo de cópia de código no editor, alternância de escopos na janela interativa e colagem manual.

## <a name="intellisense-behavior"></a>Comportamento do IntelliSense

A janela interativa inclui o IntelliSense baseado nos objetos dinâmicos, ao contrário do editor de código, no qual o IntelliSense é baseado apenas na análise de código-fonte. Isso torna as sugestões mais corretas na janela interativa, especialmente com o código gerado dinamicamente. A desvantagem é que as funções com efeitos colaterais (como mensagens de log) podem afetar sua experiência de desenvolvimento.

Se isso for um problema, altere as configurações em **Ferramentas > Opções > Ferramentas Python > Janelas Interativas** no grupo **Modo de Preenchimento**:

- **Nunca avaliar expressões**: usa o mecanismo normal do IntelliSense para obter sugestões.
- **Nunca avaliar expressões que contêm chamadas** (padrão): expressões simples como `a.b` são avaliadas, mas expressões que envolvem chamadas, como `a().b`, usam o mecanismo normal.
- **Sempre avaliar expressões**: executa a expressão completa para obter sugestões, independentemente se ela tiver efeitos colaterais.
