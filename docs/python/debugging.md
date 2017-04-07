---
title: "Depuração nas Ferramentas Python para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2192dc77-b5da-4332-b753-fa20f03f81e0
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
ms.sourcegitcommit: b0d84db6a16861fb9554af2a644423f906784748
ms.openlocfilehash: 3ca6c45cd1f61dc4a4419ab01794e24c0c19d44a
ms.lasthandoff: 03/07/2017

---

# <a name="debugging-your-python-code"></a>Depurando o código do Python

A PTVS (Ferramentas Python para Visual Studio) fornece uma experiência de depuração abrangente para o Python, incluindo a anexação a processos em execução, avaliação de expressões nas janelas Inspeção e Imediata, inspeção de variáveis locais, pontos de interrupção, instruções intervir/depuração parcial/depuração circular, comando Definir Próxima Instrução e muito mais. 

Para obter uma visão geral da depuração, assista a [Getting Started with PTVS, Part 4: Debugging](https://youtu.be/bO7wpzgy74A?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introdução à PTVS, parte 4: Depuração) (youtube.com, 3min30s).

> [!VIDEO https://www.youtube.com/embed/bO7wpzgy74A]

Neste tópico:

- [Depuração básica](#basic-debugging)
- [Opções de depuração de projeto](#project-debugging-options)
- [A janela Interativa de Depuração](#the-debug-interactive-window)

Consulte também os seguintes tópicos sobre depuração específicos ao cenário:

- [Depuração remota de plataforma cruzada](debugging-cross-platform-remote.md)
- [Depuração remota do Azure](debugging-azure-remote.md)
- [Depuração de modo misto do Python/C++](debugging-mixed-mode.md)
- [Símbolos para a depuração do modo misto](debugging-symbols-for-mixed-mode.md)

<a name="debugging-without-a-project"</a>
> [!Tip]
> A PTVS dá suporte à depuração sem um projeto. Com um arquivo independente do Python aberto no Visual Studio, clique com o botão direito do mouse no editor, selecione **Iniciar Depuração** e a PTVS iniciará o script com o ambiente global padrão (consulte [Ambientes do Python](python-environments.md)) sem nenhum argumento. Mas daí em diante, você tem suporte completo à depuração.
>
> Para controlar o ambiente e os argumentos, você precisará criar um projeto para o código. É possível fazer isso com facilidade com a opção [Com Base em um Código Existente do Python](python-projects.md#creating-a-project-from-existing-files).

<a name="debugging-with-a-project"</a>
## <a name="basic-debugging"></a>Depuração básica

O fluxo de trabalho básico de depuração envolve a definição de pontos de interrupção, a execução do código em etapas, a inspeção de valores e o tratamento de exceções, conforme descrito nas próximas seções. Para obter detalhes completos sobre o depurador do Visual Studio, consulte [Depuração no Visual Studio](../debugger/debugging-in-visual-studio.md).

Uma sessão de depuração é iniciada com o comando **Depurar > Iniciar Depuração**, o botão **Iniciar** na barra de ferramentas ou a tecla F5. Isso abrirá o arquivo de inicialização do projeto (mostrado em negrito no Gerenciador de Soluções) com o ambiente ativo do projeto e os argumentos de linha de comando ou caminhos de pesquisa especificados em Propriedades do Projeto (consulte [Opções de depuração de projeto](#project-debugging-options)).

> [!Note]
> O depurador sempre é iniciado com o ambiente ativo do Python para o projeto. Para alterar o ambiente, torne outro ambiente ativo, conforme descrito em [Ambientes do Python](python-environments.md).

### <a name="breakpoints"></a>Pontos de interrupção

Os pontos de interrupção interrompem a execução de código em um ponto marcado, para que você possa inspecionar o estado do programa. Eles são definidos clicando na margem esquerda do editor de código ou clicando com o botão direito do mouse em uma linha de código e selecionando **Ponto de Interrupção > Inserir Ponto de Interrupção**. Um ponto vermelho é exibido em cada linha com um ponto de interrupção.

![Pontos de interrupção no Visual Studio](media/debugging-breakpoints.png)

Clicar no ponto vermelho ou clicar com o botão direito do mouse na linha de código e selecionar **Ponto de Interrupção > Excluir Ponto de Interrupção** remove o ponto de interrupção. Também é possível desabilitá-lo sem removê-lo usando o comando **Ponto de Interrupção > Desabilitar Ponto de Interrupção**.

> [!Note]
> Alguns pontos de interrupção do Python podem ser uma surpresa para aqueles que estão acostumados com outras linguagens. No Python, todo o arquivo é um código executável, para que o Python execute o arquivo quando ele é carregado para processar as definições de classe ou de função de nível superior. Se um ponto de interrupção tiver sido definido, você poderá descobrir que o depurador está interrompendo uma declaração de classe parcialmente. Esse é o comportamento correto, mesmo que, às vezes, seja surpreendente.

É possível personalizar as condições nas quais um ponto de interrupção é disparado, como a interrupção somente quando uma variável atingiu determinado valor. Para definir condições, clique com o botão direito do mouse no ponto vermelho do ponto de interrupção, selecione **Condição** e, em seguida, crie expressões usando o código do Python. Para obter detalhes completos sobre esse recurso no Visual Studio, consulte [Condições de ponto de interrupção](../debugger/using-breakpoints.md#breakpoint-conditions)

Ao configurar condições, também é possível definir **Ação** e criar uma mensagem a ser registrada na janela de saída, opcionalmente, continuando a execução automaticamente. Isso cria o que é chamado de um *tracepoint*, sem a necessidade de introduzir um código de log no aplicativo diretamente:

![Criando um tracepoint com um ponto de interrupção](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>Executando o código em etapas

Depois de interromper em um ponto de interrupção, você tem várias maneiras para executar o código em etapas ou executar blocos de código antes de interromper novamente. Esses comandos estão disponíveis em vários locais, incluindo a barra de ferramentas de depuração na parte superior, o menu **Depuração**, o menu de contexto acesso com um clique com o botão direito do mouse no editor de código e por meio de atalhos de teclado (embora nem todos os comandos estejam em todos os locais):

| Recurso | Pressionamento de tecla | Descrição |
| --- | --- | --- |
| Continue | F5 | Executa o código até chegar ao próximo ponto de interrupção. |
| Entrar em | F11 | Executa a próxima instrução e para. Se a próxima instrução for uma chamada a uma função, o depurador parará na primeira linha da função que está sendo chamada. |
| Depuração Parcial | F10 | Executa a próxima instrução, incluindo fazer uma chamada a uma função (executando todo o código) e aplicar qualquer valor retornado. A depuração parcial permite ignorar facilmente as funções que não precisam ser depuradas. |
| Depuração Circular | Shift+F11 | Executa o código até o final da função atual e, em seguida, executa em etapas até a instrução de chamada. Isso é útil quando não é necessário depurar o restante da função atual. |
| Executar até o cursor | Ctrl+F10 | Executa o código até a localização do cursor no editor. Isso permite ignorar facilmente um segmento de código que não precisa ser depurado. |
| Definir próxima instrução | Ctrl+Shift+F10 | Altera o ponto de execução atual no código para a localização atual do cursor. Isso permite omitir um segmento de código de ser executado, como quando você sabe que ele tem uma falha ou produz um efeito colateral indesejado. |
| Mostrar Próxima Instrução | Alt+Num * | Retorna à próxima instrução que será executada. Isso é muito útil se você está procurando em várias partes do código e não sabe em qual parte o depurador foi realmente interrompido. |

### <a name="inspecting-and-modifying-values"></a>Inspecionando e modificando valores

Quando estiver parado no depurador, é possível inspecionar e modificar os valores das variáveis. Também é possível usar a janela Inspeção para monitorar variáveis individuais, bem como expressões personalizadas. (Consulte [Inspecionar variáveis](../debugger/getting-started-with-the-debugger.md#BKMK_Inspect_Variables) para obter detalhes gerais.)

Para exibir um valor usando DataTips, basta focalizar qualquer variável no editor. É possível clicar no valor para alterá-lo:

![DataTips no depurador](media/debugging-quick-tips.png)

A janela Automáticos (**Depurar > Janelas > Automáticos**) contém variáveis e expressões que estão próximas à instrução atual. É possível clicar duas vezes na coluna de valor ou selecionar e pressionar F2 para editar o valor:

![Janela Automáticos no depurador](media/debugging-autos-window.png)

A janela Locais (**Depurar > Janelas > Locais**) exibe todas as variáveis que estão no escopo atual, que podem ser editadas novamente:

![Janela Locais no depurador](media/debugging-locals-window.png)

Para obter mais informações sobre como usar Automáticos e Locais, consulte [Inspecionando variáveis nas janelas Automáticas e Locais](../debugger/autos-and-locals-windows.md).

A janela Inspeção (**Depurar > Janelas > Inspeção > Inspecionar 1-4**) permite inserir expressões arbitrárias do Python e exibir os resultados. As expressões são reavaliadas para cada etapa:

![Janela Inspeção no depurador](media/debugging-watch-window.png)

Para obter mais informações sobre como usar a janela Inspeção, consulte [Configurando uma inspeção em variáveis usando as janelas Inspeção e QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Ao inspecionar um valor de cadeia de caracteres (`str`, `unicode`, `bytes` e `bytearray` são considerados cadeias de caracteres para essa finalidade), você verá um ícone de lupa do lado direito do valor. Se você clicar nele, o valor de cadeia de caracteres sem aspas será exibido em uma caixa de diálogo pop-up, com encapsulamento e rolagem, o que é útil para cadeias de caracteres longas. Além disso, se você clicar na seta suspensa no ícone, poderá selecionar visualizações de texto sem formatação, HTML, XML e JSON:

![Visualizadores de cadeia de caracteres](media/debugging-string-visualizers.png)

As visualizações de HTML, XML e JSON são exibidas em janelas pop-up separadas com modos de exibição de árvore e realce de sintaxe.

### <a name="exceptions"></a>Exceções

Se ocorrer um erro enquanto o programa estiver sendo depurado e você não tiver um manipulador de exceção para ele, o depurador interromperá no ponto da exceção:

![Pop-up de exceção](media/debugging-exception-popup.png)

Neste ponto, é possível inspecionar o estado do programa, incluindo a pilha de chamadas. No entanto, se você tentar executar o código em etapas, a exceção continuará sendo gerada até que ela seja tratada ou o programa seja encerrado.

O comando de menu **Depurar > Janelas > Configurações de Exceção** abre uma janela na qual é possível expandir **Exceções do Python**:

![Janela Exceções](media/debugging-exception-settings.png)

A caixa de seleção de cada exceção controla se o depurador *sempre* interrompe quando é acionado. Marque essa caixa quando desejar interromper com mais frequência para uma exceção específica.

Por padrão, a maioria das exceções interromperá quando um manipulador de exceção não puder ser encontrado no código-fonte. Para alterar esse comportamento, clique com o botão direito do mouse em qualquer exceção e marque ou desmarque a opção “Continuar Quando Não For Tratada no Código do Usuário”. Desmarque essa caixa quando desejar interromper com menos frequência para uma exceção.

Para configurar uma exceção que não aparece nessa lista, clique no botão **Adicionar** para adicioná-la. O nome deve corresponder ao nome completo da exceção.

## <a name="project-debugging-options"></a>Opções de depuração de projeto

Por padrão, o depurador inicia o programa com o inicializador padrão do Python, sem argumentos de linha de comando e sem nenhum outro caminho ou condição especial. Eles podem ser alterados por meio das propriedades de depuração do projeto, acessadas ao clicar com o botão direito do mouse no seu projeto, no Gerenciador de Soluções, selecionando **Propriedades** e a guia **Depuração**.

![Propriedades de depuração de projeto](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opções de modo de inicialização

As opções **Modo de inicialização** permitem escolher dentre as seguintes opções, que habilitam cenários diferentes:

| Opção | Descrição |
| --- | --- |
| Inicializador padrão do Python | Usa o código de depuração escrito no Python portátil que é compatível com o CPython, IronPython e variantes como o Stackless Python. Fornece a melhor experiência de depuração de código puro do Python. Ao se anexar a um processo `python.exe` em execução, esse inicializador é usado. Esse iniciador também fornece a [depuração de modo misto](debugging-mixed-mode.md) para o CPython, permitindo a execução em etapas direta entre o código do C/C++ e o código do Python. |
| Inicializador da Web | Inicia o navegador padrão na inicialização e habilita a depuração de modelos. Consulte a seção [Depuração de modelos da Web](template-web.md#debugging) para obter mais informações. |
| Inicializador da Web do Django | Idêntico ao inicializador da Web e mostrado apenas para compatibilidade com versões anteriores. |
| Inicializador do IronPython (.NET) | Usa o depurador do .NET, que funciona somente com o IronPython, mas que permite a execução em etapas entre qualquer projeto de linguagem .NET, incluindo C# e VB. Esse inicializador é usado se você se anexa a um processo em execução do .NET que hospeda o IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opções de execução (caminhos de pesquisa, argumentos de inicialização e variáveis de ambiente)

| Opção | Descrição |
| --- | --- |
| Caminhos de Pesquisa | Eles corresponderem ao que é mostrado no nó Caminhos de Pesquisa do projeto no Gerenciador de Soluções. É possível modificar esse valor aqui, mas é mais fácil usar o Gerenciador de Soluções, que permite procurar pastas e converter os caminhos automaticamente no formato relativo. |
| Argumentos de script | Eles são adicionados ao comando usado para iniciar o script, aparecendo após o nome de arquivo do script. O primeiro item aqui estará disponível para o script como `sys.argv[1]`, o segundo como `sys.argv[2]` e assim por diante. |
| Argumentos do interpretador | Eles são adicionados à linha de comando do inicializador antes do nome do script. Os argumentos comuns aqui são `-W ...` para controlar avisos, `-O` para otimizar o programa ligeiramente e `-u` para usar o E/S não armazenado em buffer. Provavelmente, os usuários do IronPython usarão esse campo para passar opções `-X`, como `-X:Frames` ou `-X:MTA`. |
| Caminho do Interpretador | Substitui o caminho associado ao ambiente atual. Isso pode ser útil para iniciar o script com um interpretador não padrão. |
| Variáveis de ambiente | Nessa caixa de texto multilinha, adicione entradas com o formato `NAME=VALUE`. Essa configuração é aplicada por último, na parte superior das variáveis de ambiente globais existentes e depois que `PYTHONPATH` é definido de acordo com a configuração de Caminhos de Pesquisa; portanto, ela pode ser usada para substituir qualquer um deles manualmente. |

<a name="the-debug-interactive-window"</a>
## <a name="immediate-and-interactive-windows"></a>Janelas imediata e interativa

Há duas janelas interativas que podem ser usadas durante uma sessão de depuração: a janela Imediata padrão do Visual Studio e a janela Interativa de Depuração do Python.

A janela Imediata (**Depurar > Janelas > Imediata**) é usada para avaliação rápida de expressões do Python e para inspeção ou atribuição de variáveis no programa em execução. Consulte o tópico geral [Janela Imediata](../ide/reference/immediate-window.md) para obter detalhes.

A janela Interativa de Depuração do Python (**Depurar > Janelas > Interativa de Depuração do Python**) é mais avançada, pois disponibiliza toda a experiência de [REPL Interativo](interactive-repl.md) durante a depuração, incluindo a escrita e execução de código. Ela se conecta automaticamente a qualquer processo iniciado no depurador usando o inicializador padrão do Python (incluindo os processos anexados por meio de **Depurar > Anexar ao Processo*). No entanto, ela não está disponível ao usar a depuração de modo misto do C/C++.

![Janela Interativa de Depuração do Python](media/debugging-interactive.png)

A janela Interativa de Depuração dá suporte a metacomandos especiais, além dos [comandos REPL padrão](interactive-repl.md#meta-commands):

| Comando | Arguments | Descrição |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Inicia a execução do programa da instrução atual. |
| `$down`, `$d` | Move o quadro atual um nível para baixo no rastreamento de pilha. |
| `$frame` | | Exibe a ID de quadro atual.
| `$frame` | ID de quadro | Muda a ID de quadro atual para a ID de quadro especificada.
| `$load` | Carrega comandos do arquivo e os executa até a conclusão |
| `$proc` |  | Exibe a ID de processo atual. |
| `$proc` | ID de processo | Muda a ID de processo atual para a ID de processo especificada. |
| `$procs` | | Lista os processos que estão sendo depurados no momento. |
| `$stepin`, `$step`, `$s` | Intervém na próxima chamada de função, se possível. |
| `$stepout`, `$return`, `$r` | Encaminha-se para fora da função atual. |
| `$stepover`, `$until`, `$unt` | Depura parcialmente a próxima chamada de função. |
| `$thread` | | Exibe a ID de thread atual. |
| `$thread` | ID de thread | Muda a ID de thread atual para a ID de thread especificada. |
| `$threads` | | Lista os threads que estão sendo depurados no momento. |
| `$up`, `$u` | | Move o quadro atual um nível para cima no rastreamento de pilha. |
| `$where`, `$w`, `$bt` | Lista os quadros do thread atual. |

Observe que as janelas padrão do depurador, como Processos, Threads e Pilha de Chamadas não são sincronizadas com a janela Interativa de Depuração. Isso significa que a alteração do processo, thread ou quadro ativo na janela Interativa de Depuração não afetará as outras janelas do depurador. Da mesma forma, a alteração do processo, thread ou quadro ativo nas outras janelas do depurador não afetará a janela Interativa de Depuração.

A janela Interativa de Depuração tem seu próprio conjunto de opções, que pode ser acessado por meio de **Ferramentas > Opções > Ferramentas Python > Janela Interativa de Depuração**. Ao contrário da janela Interativa normal do Python, que tem uma instância separada para cada ambiente do Python, há apenas uma janela Interativa de Depuração e ela sempre usa o interpretador do Python do processo que está sendo depurado.

![Opções da Janela Interativa de Depuração](media/debugging-interactive-options.png)
