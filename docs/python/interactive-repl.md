---
title: REPL interativo do Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 69943d19c0eec4702285d255ce0c26defde79b1c
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="working-with-the-python-interactive-window"></a>Trabalhando com a Janela Interativa do Python

O Visual Studio fornece uma janela interativa REPL (leitura-avaliação-impressão-loop) para cada um dos ambientes do Python, que é uma melhoria do REPL obtido com `python.exe` na linha de comando. A janela interativa (aberta com os comandos de menu **Exibir > Outras Janelas > Interativa do &lt;ambiente&gt;**) permite que você insira o código Python arbitrário e veja resultados imediatos. Esse modo de codificação ajuda a você aprender e experimentar com APIs e bibliotecas e a desenvolver de forma interativa o código funcional para incluir em seus projetos.

![Janela interativa do Python](media/interactive-window.png)

O Visual Studio tem diversos modos REPL do Python à sua disposição:

| REPL | Descrição | Edição | Depuração | Imagens |
| --- | --- | --- | --- | --- |
| Padrão | REPL padrão, que se comunica com o Python diretamente | Edição padrão (várias linhas etc.). | Sim, por meio de `$attach` | Não |
| Depurar | REPL padrão, que se comunica com o processo depurado do Python | Edição padrão | Somente depuração | Não |
| IPython | O REPL se comunica com o back-end do IPython | Comandos do IPython, funcionalidades do Pylab | Não | Sim, embutido no REPL |
| IPython sem Pylab | O REPL se comunica com o back-end do IPython | IPython padrão | Não | Sim, em uma janela separada | 

Este tópico descreve os modos REPL **Padrão** e **Depuração**. Para obter detalhes sobre os modos do IPython, consulte [Usando o REPL do IPython](interactive-repl-ipython.md).

Para obter instruções detalhadas com exemplos, incluindo as interações com o editor, como Ctrl+Enter, consulte [Introdução – Usando uma janela interativa REPL](getting-started.md#using-the-interactive-repl-window). Para obter uma introdução em vídeo, consulte [Getting Started with Python in Visual Studio, Part 5: Interactive REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introdução ao Python no Visual Studio, parte 5: REPL interativo) (youtube.com, 2min51s).

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>Abrindo uma janela interativa

Há várias maneiras para abrir a janela interativa de um ambiente.

Em primeiro lugar, mude para a janela Ambientes do Python (**Exibir > Outras Janelas > Ambientes do Python** ou Ctrl-K, Ctrl-`) e selecione o comando ou botão **Abrir Janela Interativa** para um ambiente escolhido.

![Link Janela Interativa na janela Ambientes do Python](media/interactive-window-opening.png)

Em segundo lugar, próximo à parte inferior do menu **Exibir > Outras Janelas**, há um comando **Janela Interativa do Python** para seu ambiente padrão, bem como um comando para alternar para a janela de ambientes:

![Itens de menu da Janela Interativa em Exibir > Outras Janelas](media/interactive-window-menu.png)

Em terceiro lugar, é possível abrir uma janela interativa no arquivo de inicialização do projeto ou para um arquivo independente, selecionando o comando de menu **Depurar > Executar [Projeto | Arquivo] em Python Interativo** (Shift+Alt+F5):

![Executar Projeto no menu Python Interativo](media/interactive-execute-project.png)

Por fim, é possível selecionar o código no arquivo e usar o [comando Enviar código para interativa](#send-code-to-interactive-command) descrito abaixo.

## <a name="interactive-window-options"></a>Opções da janela interativa

Você pode controlar vários aspectos da janela interativa por meio de **Ferramentas > Opções > Ferramentas Python > Janelas Interativas** (consulte [Opções](options.md)):

![Opções da janela interativa do Python](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Usando a janela interativa

Depois de abrir a janela interativa, é possível começar a inserir o código linha por linha no prompt `>>>`. A janela interativa executa cada linha conforme ela é inserida, o que inclui a importação de módulos, definição de variáveis e assim por diante:

![Janela interativa do Python](media/interactive-window.png)

A exceção é quando as linhas de código adicionais são necessárias para fazer uma instrução completa, como quando uma instrução `for` termina em dois pontos como mostrado acima. Nesses casos, o prompt de linha muda para `...`, indicando que é necessário inserir linhas adicionais no bloco, conforme mostrado na quarta e quinta linhas do gráfico acima. Ao pressionar Enter em uma linha em branco, a janela interativa fecha o bloco e o executa no interpretador.

> [!Tip]
> A janela interativa é uma melhoria da experiência comum do REPL de linha de comando do Python, recuando automaticamente as instruções que pertencem a um escopo ao redor. Seu histórico (recuperado com a seta para cima) também fornece itens de várias linhas, enquanto o REPL de linha de comando fornece somente linhas individuais.

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

Os comandos também são extensíveis pelas extensões do Visual Studio implementando e exportando `IInteractiveWindowCommand` ([exemplo](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switching-scopes"></a>Mudando escopos

Por padrão, a janela interativa de um projeto tem como escopo o arquivo de inicialização do projeto, como se ele fosse executado no prompt de comando. Para um arquivo independente, ele tem como escopo esse arquivo. No entanto, a qualquer momento, o menu suspenso na parte superior da janela interativa permite alterar o escopo durante a sessão de REPL:

![Escopos da janela interativa](media/interactive-scopes.png)

Ao importar um módulo, como digitando `import importlib`, você verá opções na lista suspensa para mudar para qualquer escopo nesse módulo. Uma mensagem na janela interativa também indica o novo escopo, portanto, é possível acompanhar como você chegou a um determinado estado durante sua sessão.

A inserção de `dir()` em um escopo exibe os identificadores válidos no escopo, incluindo nomes de função, classes e variáveis. Por exemplo, o uso de `import importlib` seguido por `dir()` mostra o seguinte:

![Janela interativa no escopo de importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Comando Enviar código para interativa

Além de trabalhar na janela interativa diretamente, é possível selecionar o código no editor, clicar com o botão direito do mouse e escolher **Enviar para o Interativo** ou pressione Ctrl+Enter.

![Comando de menu Enviar para interativa](media/interactive-send-to.png)

Esse comando é útil para o desenvolvimento de código iterativo ou evolucionário, incluindo o teste do código durante o desenvolvimento. Por exemplo, depois de enviar um trecho de código para a janela interativa e ver sua saída, é possível pressionar a seta para cima para exibir o código novamente, modificá-lo e testá-lo rapidamente pressionando Ctrl+Enter. (Pressionar Enter no final da entrada o executa, mas pressionar Enter no meio da entrada insere uma nova linha.) Depois de obter o código desejado, é possível copiá-lo novamente com facilidade para o arquivo de projeto.

> [!Tip]
> Por padrão, o Visual Studio remove >>> e ... O REPL solicita ao colar o código da janela interativa no editor. Você pode alterar esse comportamento na guia **Ferramentas > Opções > Editor de Texto > Python > Avançado** usando a opção **Colar remove os prompts REPL**. Consulte [Opções – Opções diversas](options.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

Ao usar um arquivo de código como um bloco de rascunho, geralmente você tem um pequeno bloco de código que você deseja enviar de uma só vez. Para agrupar códigos, marque o código como uma *célula de código* adicionando um comentário começando com `#%%` ao início da célula, que termina a anterior. Células de código podem ser recolhidas e expandidas e usar Ctrl+Enter dentro de uma célula de código envia toda a célula para a janela interativa e passa para o próximo.

O Visual Studio também detecta células de código começando com comentários como `# In[1]:`, que é o formato que você obtém ao exportar um bloco de anotações do Jupyter como um arquivo do Python. Essa detecção torna mais fácil executar um bloco de anotações do [Notebooks do Azure](https://notebooks.azure.com/) baixando como um arquivo Python, abrindo no Visual Studio e usando Ctrl+Enter para executar cada célula.

![Células de código interativas](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Comportamento do IntelliSense

A janela interativa inclui o IntelliSense baseado nos objetos dinâmicos, ao contrário do editor de código, no qual o IntelliSense é baseado apenas na análise de código-fonte. Essas sugestões são mais corretas na janela interativa, especialmente com o código gerado dinamicamente. A desvantagem é que as funções com efeitos colaterais (como mensagens de log) podem afetar sua experiência de desenvolvimento.

Se esse comportamento for um problema, altere as configurações em **Ferramentas > Opções > Ferramentas Python > Janelas Interativas** no grupo **Modo de Conclusão**, conforme descrito em [Opções – Opções das Janelas Interativas](options.md#interactive-windows-options).

