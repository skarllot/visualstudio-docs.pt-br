---
title: "Opções do Python no Visual Studio | Microsoft Docs\""
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c714867-7a64-4b1e-aca8-09d956192279
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: a71d076e85e1e7ae070014e83186c0011ca9e58f
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="options-for-python-in-visual-studio"></a>Opções para o Python no Visual Studio

Para exibir as opções do Python, use o comando de menu **Ferramentas > Opções**, verifique se **Mostrar todas as configurações** está selecionado e navegue até **Ferramentas do Python**:

![Caixa de diálogo de opções do Python, guia Geral](media/options-general.png)

Também há opções adicionais específicas do Python na guia **Editor de Texto > Python > Avançado**.

As opções específicas são descritas nas seguintes seções:

- [Opções gerais](#general-options)
- [Opções de depuração](#debugging-options)
- [Opções da Janela Interativa](#interactive-windows-options)
- [Opções avançadas de editor de Python](#advanced-python-editor-options)

## <a name="general-options"></a>Opções gerais

| Opção | Padrão | Descrição |
| --- | --- | --- |
| Mostrar a Janela de Saída ao criar ambientes virtuais| On | Desmarque essa opção para impedir que a janela de saída apareça. |
| Mostrar a Janela de Saída ao instalar ou remover pacotes | On |  Desmarque essa opção para impedir que a janela de saída apareça. |
| Sempre executar pip como administrador | Off | Sempre eleva as operações `pip install` para todos os ambientes. Ao instalar pacotes, o Visual Studio solicitará privilégios de administrador se o ambiente estiver localizado em uma área protegida do sistema de arquivos como `c:\Program Files`. Nesse prompt, você pode optar por sempre elevar `pip install` apenas para esse ambiente específico. Consulte [Ambientes do Python – guia pip](python-environments.md#pip-tab). |
| Gerar automaticamente o BD de conclusão no primeiro uso | On | Para as [conclusões do IntelliSense](code-editing.md#intellisense) funcionarem para uma biblioteca, o Visual Studio deve gerar um banco de dados de conclusão para essa biblioteca. A criação do banco de dados é feita em segundo plano quando uma biblioteca é instalada, mas não pode ser concluída quando você começa a escrever código. Com esta opção selecionada, o Visual Studio prioriza a conclusão do banco de dados para uma biblioteca quando você escreve código que a usa. |
| Ignorar variáveis PYTHONPATH de todo o sistema | On | PYTHONPATH é ignorado por padrão porque o Visual Studio fornece um meio mais direto para especificar caminhos de pesquisa em projetos e ambientes. Consulte [Ambientes do Python – caminhos de pesquisa](python-environments.md#search-paths) para obter detalhes. |
| Atualizar os caminhos de pesquisa ao adicionar arquivos vinculados | On | Quando definido, adicionar um [arquivo vinculado](python-projects.md#linked-files) a um projeto atualiza os [caminhos de pesquisa](python-environments.md#search-paths) para que o IntelliSense possa incluir o conteúdo da pasta do arquivo vinculado em seu banco de dados de conclusão. Desmarque esta opção para excluir o conteúdo do banco de dados de conclusão. |
| Avisar quando o módulo importado não puder ser encontrado | On | Desmarque esta opção para suprimir avisos quando você sabe que um módulo importado não está disponível no momento, mas não afeta a operação do código de outra forma. |
| Relatar recuo divergente como | Avisos | Como o interpretador do Python depende muito do recuo adequado para determinar o escopo, o Visual Studio por padrão emite avisos quando detecta recuos inconsistentes que podem indicar erros de codificação. Definir como *Erros* para ser ainda mais estrito, o que faz com que o programa saia nesses casos. Para desabilitar esse comportamento completamente, selecione *Não*. |
| Verificar se há pesquisa/notícias | Uma vez por semana | Define a frequência com que você permite que o Visual Studio possa abrir uma janela contendo uma página da Web com itens de notícias e pesquisas relacionados ao Python, se disponível. As opções são *Nunca*, *Uma vez por dia*, *Uma vez por semana* e *Uma vez por mês*. |
| Redefinir todas as caixas de diálogo permanentemente ocultas (botão) | N/D | Caixas de diálogo diferentes fornecem opções como **Não mostrar novamente**. Use esse botão para limpar essas opções e fazer com que as caixas de diálogo sejam exibidas novamente. |

![Caixa de diálogo de opções do Python, guia Geral](media/options-general.png)

## <a name="debugging-options"></a>Opções de depuração

| Opção | Padrão | Descrição |
| --- | --- | --- |
| Perguntar antes de executar quando houver erros | On | Quando definido, solicita que você confirme que deseja executar o código que contém erros. Desmarque esta opção para desabilitar o aviso. |
| Aguardar pela entrada quando o processo for encerrado de forma anormal<br/><br/>Aguardar pela entrada quando o processo for encerrado normalmente | Ativo (para os dois) | Um programa de Python iniciado no Visual Studio é executado em sua própria janela de console. Por padrão, a janela espera que você pressione uma tecla antes de fechá-la, independentemente de como o programa é encerrado. Para remover este prompt e fechar a janela automaticamente, desmarque uma ou ambas as opções. |
| A saída do programa para Depurar a janela de Saída | On | Exibe a saída do programa em uma janela separada do console e na janela de saída do Visual Studio. Desmarque esta opção para mostrar a saída somente na janela do console separado. |
| Interromper a exceção SystemExit com código de saída zero | Off | Se definido, interrompe o depurador nessa exceção. Quando desmarcado, o depurador sai sem interromper. |
| Habilitar a depuração da biblioteca padrão do Python | Off | Torna possível intervir no código-fonte da biblioteca padrão durante a depuração, mas aumenta o tempo necessário para iniciar o depurador.|

![Caixa de diálogo de opções do Python, guia Depuração](media/options-debugging.png)

## <a name="interactive-windows-options"></a>Opções da Janela Interativa

| Opção | Padrão | Descrição |
| --- | --- | --- |
| Scripts | N/D | Especifica uma pasta geral para scripts de inicialização aplicar a serem aplicados às janelas interativas para todos os ambientes. Consulte [Scripts de inicialização](python-environments.md#startup-scripts). No entanto, observe que esse recurso não funciona no momento. |
| As setas para cima e para baixo navegam o histórico | On | Usa as teclas de direção para navegar no histórico na janela interativa. Desmarcar essa configuração para usar as teclas de direção na saída da janela interativa. |
| Modo de Conclusão | Avaliar somente expressões sem função chamadas | O processo de determinar os membros disponíveis em uma expressão na janela interativa pode exigir a avaliação da expressão incompleta atual, que pode resultar em efeitos colaterais ou funções sendo chamadas várias vezes. A configuração padrão *Avaliar somente expressões sem função chamadas* exclui expressões que aparecem para chamar uma função, mas avaliada outras expressões. Por exemplo, ele avalia `a.b`, mas não `a().b`.  *Nunca avaliar expressões* impede todos os efeitos colaterais, usando apenas o mecanismo IntelliSense normal para obter sugestões. *Avaliar todas as expressões* avalia a expressão completa para obter sugestões, independentemente de efeitos colaterais. |
| Ocultar sugestões de análise estática | Off | Quando definido, exibe apenas sugestões que são obtidas avaliando a expressão. Se combinado com o Modo de Conclusão *Nunca avaliar expressões*, não aparece nenhuma conclusão útil na janela interativa. |

![Caixa de diálogo de opções do Python, guia Janelas Interativas](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Opções avançadas de editor de Python

### <a name="completion-results"></a>Resultados de Conclusão

| Opção | Padrão | Descrição |
| --- | --- | --- |
| A conclusão de membro exibe a interseção de membros | Off | Quando definido, mostra apenas conclusões que têm suporte por todos os tipos possíveis. |
| Lista de filtro com base na cadeia de pesquisa | On | Aplica a filtragem de sugestões de preenchimento conforme você digita (o padrão é marcado). |
| Mostra automaticamente preenchimentos para todos os identificadores | On | Desmarque esta opção para desabilitar as conclusões no editor e nas janelas interativas. |

### <a name="selection-in-completion-list"></a>Seleção em listas de conclusão

| Opção | Padrão | Descrição |
| --- | --- | --- |
| Confirmado pela digitação dos seguintes caracteres | {}[]().,:;+-*/%&&#124;^~=<>#@\ | Esses caracteres normalmente seguem um identificador que pode ser selecionado em uma lista de conclusão, portanto, é conveniente confirmar a conclusão digitando um caractere. Você pode remover ou adicionar caracteres específicos à lista conforme desejado.  |
| Inserir a conclusão atual de confirmação | On | Quando definido, a tecla Enter escolhe e aplica a conclusão selecionada no momento, assim como acontece com os caracteres acima (mas obviamente, não há um caractere para Enter portanto, ele não pode entrar diretamente para essa lista!). |
| Adicionar uma nova linha ao pressionar Enter após o fim da palavra totalmente digitada | Off | Por padrão, se você digitar a palavra inteira que aparece no pop-up de conclusão e pressionar Enter, você confirmará a conclusão. Definindo essa opção, você efetivamente confirmar conclusões quando terminar de digitar o identificador que Enter insere uma nova linha. |

### <a name="miscellaneous-options"></a>Opções diversas

| Opção | Padrão | Descrição |
| --- | --- | --- |
| Entre no modo estrutura de tópicos quando os arquivos abrem | On | Ative automaticamente o recurso de estrutura de tópicos do Visual Studio no editor ao abrir o arquivo de código do Python. |
| Colar prompts REPL removidos | On | Remove >>> e ... do texto colado, permitindo a transferência fácil do código da janela interativa para o editor. Desmarque essa opção se você precisar manter esses caracteres ao colar de outras fontes. |
| Nomes de cores com base em tipos | On | Habilita as cores de sintaxe no código do Python. |

![Caixa de diálogo de opções do editor do Python, guia Avançado](media/options-editor-advanced.png)
