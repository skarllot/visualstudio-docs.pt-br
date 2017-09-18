---
title: "Editando o código do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03effe56-d6f6-461d-9005-e43c15bf537c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: d16b8fcae5b7d1a14c8f6068dfd7103115cba291
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="editing-python-code"></a>Editando o código do Python

Os desenvolvedores passam muito tempo no editor de código, portanto o [Suporte a Python no Visual Studio](installation.md) fornece funcionalidade para ajudá-lo a ser mais produtivo. Os recursos incluem o realce de sintaxe do IntelliSense, o preenchimento automático, a ajuda da assinatura, as substituições de método, a pesquisa e a navegação. 

Neste tópico:

- [IntelliSense](#intellisense) incluindo preenchimentos, ajuda da assinatura, informações rápidas e coloração de código.
- [Trechos de código](#code-snippets)
- [Navegando pelo código](#navigating-your-code)

Para obter uma documentação geral sobre como editar o código no Visual Studio, consulte [Escrevendo código no editor de código e de texto](../ide/writing-code-in-the-code-and-text-editor.md). Consulte também [Estrutura de tópicos no Visual Studio](../ide/outlining.md), que ajuda você a manter o foco em seções específicas do código. O suporte do Python inclui o uso do Pesquisador de Objetos do Visual Studio (**Exibir > Outras Janelas > Pesquisador de Objetos** ou Ctrl+W, J) para inspecionar as classes definidas em cada módulo e as funções definidas nessas classes. 

O editor também é integrado à janela interativa no Visual Studio, tornando mais fácil trocar o código entre as duas. Consulte [Introdução – Usando uma janela interativa REP]) (getting-started.md#using-the-interactive-repl-window) e [Usando a janela interativa – Enviar código para o comando interativo](interactive-repl.md#send-code-to-interactive-command) para obter detalhes.

Para obter uma introdução à edição de código Python, assista à [Getting Started with Python in Visual Studio, Part 3: Editing](https://youtu.be/uZGZNEyyeKs?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Introdução ao Python no Visual Studio, parte 3: edição) (youtube.com, 3min48s):

> [!VIDEO https://www.youtube.com/embed/uZGZNEyyeKs]

## <a name="intellisense"></a>IntelliSense

O IntelliSense fornece [preenchimentos](#completions), [ajuda da assinatura](#signature-help), [informações rápidas](#quick-info) e [coloração de código](#code-coloring). Para melhorar o desempenho, o IntelliSense depende do banco de dados de preenchimento que é gerado para cada ambiente do Python no projeto. Os bancos de dados podem precisar de atualização se você adicionar, remover ou atualizar os pacotes. O status do banco de dados é mostrado na janela **Ambientes do Python** (um irmão do Gerenciador de Soluções) da guia **IntelliSense** (consulte [Ambientes do Python](python-environments.md)). 

### <a name="completions"></a>Preenchimentos

Preenchimentos aparecem como instruções, identificadores e outras palavras que podem ser inseridas adequadamente na localização atual no editor. O que é mostrado na lista baseia-se no contexto e é filtrado para omitir opções incorretas ou que desviam a atenção. Em geral, os preenchimentos são disparados com a digitação de instruções diferentes (como `import`) e operadores (incluindo um ponto final), mas é possível fazer com que eles apareçam a qualquer momento digitando Ctrl-J, Espaço.

![Preenchimento de membro](media/code-editing-completions-simple.png)

Quando uma lista de preenchimento é aberta, é possível pesquisar o preenchimento que você deseja usando as teclas de direção, o mouse ou continuando a digitação. Conforme você digita mais letras, a lista é filtrada ainda mais para mostrar os prováveis preenchimentos. Você também pode usar atalhos, como:

- Digitar letras que não estão no início do nome, como “parse” para encontrar “argparse”
- Digitar apenas letras que estão no início de palavras, como “abc” para encontrar “AbstractBaseClass” ou “air” para encontrar “as_integer_ratio”
- Ignorar letras, como “b64” para encontrar “base64”

Alguns exemplos:

![Preenchimento de membro com filtragem](media/code-editing-completion-filtering.png)

Os preenchimentos de membro aparecem automaticamente quando você digita um ponto final depois de uma variável ou um valor, juntamente com os métodos e os atributos dos tipos possíveis. Se uma variável puder ser de mais de um tipo, a lista incluirá todas as possibilidades de todos os tipos, com informações extras para indicar quais tipos dão suporte a cada preenchimento. Quando um preenchimento tem o suporte de todos os tipos possíveis, ele é mostrado sem anotação.

![Preenchimento de membro em vários tipos](media/code-editing-completion-types.png)

Por padrão, os membros “dunder” (membros que começam e terminam com um sublinhado duplo) não são mostrados. Em geral, esses membros não devem ser acessados diretamente. Se você precisar de um, no entanto, digitar o sublinhado duplo à esquerda adiciona esses preenchimentos à lista:

![Preenchimento de membro privado](media/code-editing-completion-dunder.png)

As instruções `import` e `from ... import` exibem uma lista de módulos que podem ser importados. Com `from ... import`, a lista inclui os membros que podem ser importados do módulo especificado.

![Preenchimento de importação](media/code-editing-completion-import.png)

As instruções `raise` e `except` exibem listas de classes que provavelmente são tipos de erros. A lista pode não incluir todas as exceções definidas pelo usuário, mas ajuda você a encontrar as exceções internas adequadas rapidamente:

![Preenchimento de exceção](media/code-editing-completion-exception.png)

Digitar @ inicia um decorador e mostra os decoradores possíveis. Muitos desses itens não podem ser usados como decoradores, verifique a documentação da biblioteca para determinar qual deles usar.

![Preenchimento de decorador](media/code-editing-completion-decorator.png)

> [!Tip]
> É possível configurar o comportamento de preenchimentos por meio de **Ferramentas > Opções > Editor de Texto > Python > Avançado**. Dentre eles, **Filtrar lista com base na cadeia de caracteres de pesquisa**: aplica a filtragem de sugestões de preenchimento à medida que você digita (o padrão é marcado); **Preenchimento de membro exibe a interseção dos membros** mostra apenas os preenchimentos que têm suporte em todos os tipos possíveis (o padrão é desmarcado). Consulte [Opções – Resultados de Conclusão](options.md#completion-results).

### <a name="signature-help"></a>Ajuda da assinatura

Ao escrever o código que chama uma função, a ajuda da assinatura é exibida quando você digita o `(` de abertura e exibe as informações de parâmetro e documentação disponíveis. Também é possível fazer com ela seja exibida com Ctrl+Shift+Espaço dentro de uma chamada de função. As informações exibidas dependem das cadeias de caracteres de documentação no código-fonte da função, mas incluem os valores padrão.

![Ajuda da assinatura](media/code-editing-signature-help.png)

> [!Tip]
> Para desabilitar a ajuda da assinatura, acesse **Ferramentas > Opções > Editor de Texto > Python > Geral** e desmarque a opção **Preenchimento de declaração > Informações de parâmetro**.

### <a name="quick-info"></a>Informações rápidas

Focalizar o ponteiro do mouse em um identificador exibe uma dica de ferramenta Informações Rápidas. Dependendo do identificador, Informações Rápidas poderá exibir os possíveis valores ou tipos, toda a documentação disponível, tipos de retorno e localizações de definição:

![Informação Rápida](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Coloração de código

A coloração de código usa informações da análise de código para colorir variáveis, instruções e outras partes do código. Por exemplo, as variáveis que se referem a módulos ou classes podem ser exibidas em uma cor diferente da de funções ou outros valores e os nomes de parâmetro são exibidos em uma cor diferente da que variáveis locais ou globais. (Por padrão, as funções não são exibidas em negrito):

![Coloração de código](media/code-editing-code-coloring.png)

Para personalizar as cores, acesse **Ferramentas > Opções > Ambiente > Fontes e Cores** e modifique as entradas do Python na lista **Exibir itens**:

![Opções de Fontes e Cores](media/code-editing-customize-colors.png)

> [!Tip]
> Para desabilitar a coloração de código, acesse **Ferramentas > Opções > Editor de Texto > Python > Avançado** e desmarque **Opções Diversas > Colorir nomes com base no tipo**. Consulte [Opções – Opções Diversas](options.md#miscellaneous-options).


## <a name="code-snippets"></a>Trechos de código

Trechos de código são fragmentos de código que podem ser inseridos nos arquivos digitando um atalho e pressionando Tab ou usando os comandos **Editar > IntelliSense > Inserir Trecho de Código** **Envolver com**. Por exemplo, digitar `class` seguido pela tecla Tab gera o restante da classe. É possível digitar sobre o nome e a lista de bases, movendo entre os campos realçados com Tab e, em seguida, pressionando Enter para começar a digitar o corpo.

![Trechos de código](media/code-editing-code-snippets.png)

É possível ver os trechos de código disponíveis no Gerenciador de Trechos de Código (**Ferramentas > Gerenciador de Trechos de Código**), selecionando **Python** como a linguagem:

![Gerenciador de Trechos de Código](media/code-editing-code-snippets-manager.png)

Para criar seus próprios trechos de código, consulte [Passo a passo: Criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md).
Trechos de código podem ser personalizados com a [criação de um trecho de código](https://msdn.microsoft.com/library/ms165394.aspx) e importando-o por meio do 

Se você escrever um ótimo trecho de código que gostaria de compartilhar, fique à vontade para postá-lo em linhas gerais e [contar para nós](https://github.com/Microsoft/PTVS/issues). Talvez possamos incluí-lo em uma versão futura do Visual Studio.


## <a name="navigating-your-code"></a>Navegando pelo código

O suporte do Python no Visual Studio fornece vários meios para navegar rapidamente no código, incluindo bibliotecas para as quais o código-fonte está disponível: a [barra de navegação](#navigation-bar), [Ir Para Definição](#go-to-definition), [Navegar Para](#navigate-to) e [Localizar Todas as Referências](#find-all-references). Também é possível usar o [Pesquisador de Objetos](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) do Visual Studio.

### <a name="navigation-bar"></a>Barra de navegação

A barra de navegação é exibida na parte superior de cada janela do editor e inclui uma lista de dois níveis de definições. A lista suspensa à esquerda contém definições de nível superior de classe e função no arquivo atual; a lista suspensa à direita exibe uma lista de definições dentro do escopo mostrado à esquerda. Conforme você usa o editor, as listas são atualizadas para mostrar o contexto atual e você também pode selecionar uma entrada dessa lista para ir diretamente para ela.

![Barra de navegação](media/code-editing-navigation-bar.png)

> [!Tip]
> Para ocultar a barra de navegação, acesse **Ferramentas > Opções > Editor de Texto > Python > Geral** e desmarque a opção **Configurações > Barra de navegação**.

### <a name="go-to-definition"></a>Ir para definição

O comando **Ir Para Definição** vai rapidamente do uso de um identificador (como um nome de função, classe ou variável) para o código-fonte em que ele está definido. Invoque-o clicando com o botão direito do mouse em um identificador e selecionando **Ir Para Definição** ou colocando o cursor no identificador e pressionando F12. Ele funciona em todo o código e nas bibliotecas externas, desde que o código-fonte esteja disponível. Se o código-fonte da biblioteca não estiver disponível, o comando **Ir Para Definição** irá para a instrução `import` relevante de uma referência de módulo ou exibirá um erro.

![Ir para definição](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Navegar para

O comando **Editar > Navegar Para...** (Ctrl-vírgula) exibe uma caixa de pesquisa no editor em que é possível digitar qualquer cadeia de caracteres e ver as possíveis correspondências no código que definem uma função, classe ou variável que contém essa cadeia de caracteres. Esse recurso fornece uma funcionalidade semelhante a **Ir Para Definição**, mas sem a necessidade de localizar um uso de um identificador.

Clicar duas vezes em um nome ou selecioná-lo com teclas de direção e Enter navegará para a definição desse identificador.

![Navegar para](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Localizar Todas as Referências

O comando **Localizar Todas as Referências** é uma maneira útil de descobrir o local em que um identificador específico é definido e usado, incluindo importações e atribuições. Invoque-o clicando com o botão direito do mouse em um identificador e selecionando **Localizar Todas as Referências** ou colocando o cursor no identificador e pressionando Shift+F12. Clicar duas vezes em um item da lista navegará para sua localização.

![Resultados de Localizar Todas as Referências](media/code-editing-find-all-references.png)
