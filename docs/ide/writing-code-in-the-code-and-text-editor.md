---
title: "Escrever código no editor de código | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7b3cc733a1a808f60a27332024bcfff1dd9e670b
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="write-code-in-the-code-editor"></a>Escrever código no editor de códigos
O editor do Visual Studio fornece muitos recursos que facilitam escrever e gerenciar seu código e texto. Você pode expandir e recolher blocos de código diferentes usando a estrutura de tópicos. Você pode aprender mais sobre o código que você está usando através do IntelliSense, do **Pesquisador de Objetos** e da Hierarquia de Chamada. Você pode localizar o código usando recursos como **Navegar Para**, **Ir para Definição** e **Localizar Todas as Referências**. Você pode inserir blocos de código com trechos de código e pode gerar código usando recursos como o **Gerar do uso**. Se você nunca usou o editor do Visual Studio, consulte [Editando seu Código](https://www.visualstudio.com/features/ide-vs) para obter uma visão geral rápida.  

 Você pode exibir seu código de várias maneiras diferentes. Para ver um modo de exibição de classe de sua solução, você pode abrir a janela **Modo de Exibição de Classe** ou expandir nós no **Gerenciador de Soluções** em seus arquivos de classe.

 Você pode pesquisar e substituir texto para um ou vários arquivos. Para obter mais informações, consulte [Localizando e substituindo texto](../ide/finding-and-replacing-text.md). É possível usar expressões regulares para localizar e substituir texto. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 As diferentes linguagens do Visual Studio oferecem conjuntos de recursos diferentes e, em alguns casos, os recursos se comportam de forma diferente nas diferentes linguagens. Muitas dessas diferenças são especificadas nas descrições dos recursos, mas para obter mais informações, consulte as seções sobre as linguagens específicas do Visual Studio.  

> [!IMPORTANT]
>  A edição do Visual Studio e as configurações que você está usando podem afetar os recursos no IDE. Eles podem ser diferentes dos descritos neste tópico.  

## <a name="editor-features"></a>Recursos do Editor  

|||  
|-|-|  
|Coloração de sintaxe|Alguns elementos de sintaxe dos arquivos de código e de marcação são coloridos de maneiras diferentes para diferenciá-los. Por exemplo, palavras-chave (como `using` no C# e `Imports` no Visual Basic) são de uma cor, mas tipos (como `Console` e `Uri`) são de outra cor. Outros elementos de sintaxe também são coloridos, como comentários e literais de cadeia de caracteres. O C++ usa cores para fazer diferenciação entre tipos, enumerações e macros, entre outros tokens.<br /><br /> Você pode ver a cor padrão de cada tipo e pode alterar a cor de qualquer elemento de sintaxe específico na [caixa de diálogo Fontes e Cores, Ambiente, Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que pode ser aberta no menu **Ferramentas**.|  
|Marcas de Erro e Aviso|Enquanto adiciona código e compila sua solução, você pode ver: (a)sublinhados ondulados de cores diferentes (conhecidos como rabiscos) ou (b) lâmpadas que aparecem em seu código. Rabiscos vermelhos indicam erros de sintaxe, azul indica erros de compilador, verde indica avisos e roxo indica outros tipos de erros. [As lâmpadas](../ide/perform-quick-actions-with-light-bulbs.md) sugerem correções para problemas e facilitam a aplicação da correção.<br /><br /> Você pode ver a cor padrão de cada rabisco de erro e de aviso na caixa de diálogo **Ferramentas/Opções/Ambiente/Fontes e Cores**. Procure por **Erro de Sintaxe**, **Erro do Compilador**, **Aviso** e **Outro Erro**.|  
|Correspondência de chave|Quando o ponto de inserção é colocado em uma chave de abertura em um arquivo de código, essa chave de abertura e a chave de fechamento são realçadas. Esse recurso fornece comentários imediatos sobre chaves no local incorreto ou ausentes. Você pode ativar ou desativar a correspondência de chaves com a configuração **Realce automático de delimitadores** (**Ferramentas/Opções/Editor de Texto**). Você pode alterar a cor do realce na configuração **Fontes e Cores** (**Ferramentas/Opções/Ambiente**). Procure **Correspondência de Chaves (Realce)** ou **Correspondência de Chaves (Retângulo)**.|  
|Visualizador de Estrutura|Linhas pontilhadas conectam chaves correspondentes nos arquivos de código, o que facilita ver a abertura e o fechamento de pares de chave. Isso pode ajudar a localizar o código em sua base de código mais rapidamente. Você pode ativar ou desativar essas linhas em **Mostrar diretrizes de estrutura** na seção **Exibição** da página **Ferramentas/Opções/Editor de Texto/Geral**.|
|Números de Linha|Os números de linha podem ser exibidos na margem esquerda da janela de código. Eles não são exibidos por padrão. Você poderá ativar essa opção nas configurações **Todas as Linguagens do Editor de Texto** (**Ferramentas/Opções/Editor de Texto/Todas as Linguagens**). Você pode exibir números de linha para linguagens de programação individuais, alterando as configurações para essas linguagens (**Ferramentas/Opções/Editor de Texto/\<linguagem>**). Para imprimir os números de linha é necessário selecionar Incluir números de linha na caixa de diálogo **Imprimir**.|  
|Controle de Alterações|A cor da margem esquerda permite que você mantenha o controle das alterações feitas em um arquivo. As alterações que foram feitas desde que o arquivo foi aberto mas não foram salvas são indicadas por uma barra amarela na margem esquerda (conhecida como a margem de seleção). Depois de salvar as alterações (mas antes de fechar o arquivo), a barra ficará verde. Se você desfizer uma alteração depois de salvar o arquivo, a barra ficará laranja. Para desativar e ativar esse recurso, altere a opção **Controlar Alterações** nas configurações **Editor de Texto** (**Ferramentas/Opções/Editor de Texto**).|  
|Seleção de código e texto|É possível selecionar texto no modo padrão de fluxo contínuo ou no modo de caixa, no qual você seleciona uma parte retangular do texto em vez de um conjunto de linhas. Para fazer uma seleção no modo de caixa, pressione a tecla ALT enquanto arrasta o mouse sobre a seleção (ou pressione ALT + SHIFT + \<tecla de direção>). A seleção inclui todos os caracteres dentro do retângulo definido pelo primeiro caractere e o último caractere na seleção. Tudo que é digitado ou colado na área selecionada é inserido no mesmo ponto em cada linha.|  
|Aplicar Zoom|Você pode ampliar ou reduzir em qualquer janela de código pressionando a tecla CTRL e, mantendo-a pressionada, mover a roda de rolagem do mouse (ou CTRL + SHIFT +. para aumentar e CTRL + SHIFT +, para diminuir). Você também pode usar a caixa de Zoom no canto inferior esquerdo da janela de código para definir um percentual específico de aplicação de zoom. O recurso de aplicar zoom não funciona em janelas de ferramentas.|  
|Espaço virtual|Por padrão, as linhas nos editores do Visual Studio terminam após o último caractere de forma que a tecla SETA PARA A DIREITA, ao final de uma linha, move o cursor para o início da próxima linha. Em alguns editores uma linha não termina depois do último caractere e é possível colocar o cursor em qualquer lugar na linha. Você pode habilitar o espaço virtual no editor nas configurações **Ferramentas/Opções/Editor de Texto/Todas as Linguagens**. Observe que você pode habilitar **Espaço virtual** ou **Quebra automática de linha**, mas não ambos.|  
|Imprimindo|Você pode usar as opções da caixa de diálogo **Imprimir** para incluir números de linha ou ocultar regiões de código recolhidas ao imprimir um arquivo. Na caixa de diálogo **Configuração de Página** também é possível imprimir o caminho completo e o nome do arquivo, escolhendo **Cabeçalho de Página**.<br /><br /> Você pode definir opções de impressão a cores na caixa de diálogo **Ferramentas/Opções/Ambiente/Fontes e Cores**. Escolha **Impressora** na lista **Mostrar configurações de** para personalizar a impressão a cores. Você pode especificar cores para imprimir um arquivo diferentes das cores para edição de um arquivo.|  
|Desfazer global e Refazer|O comandos **Desfazer Última Ação Global** e **Refazer Última Ação Global** no menu **Editar** desfazem ou refazem ações globais que afetam vários arquivos. As ações globais incluem renomeação de uma classe ou namespace, executar uma operação de localização e substituição em uma solução, refatoração de um banco de dados ou qualquer outra ação que altera vários arquivos. Você pode aplicar os comandos desfazer e refazer global para ações na sessão atual do Visual Studio, mesmo depois de fechar a solução na qual a ação foi aplicada.|  

## <a name="advanced-editing-features"></a>Recursos de edição avançada  
 Você pode encontrar uma série de recursos avançados no submenu **Editar/Avançado**. Nem todos esses recursos estão disponíveis para todos os tipos de arquivos de código.  

|||  
|-|-|  
|Formatar Documento|Define o recuo adequado das linhas de código e move as chaves para separar linhas no documento.|  
|Formatar Seleção|Define o recuo adequado das linhas de código e move as chaves para separar linhas na seleção.|  
|Tabular linhas selecionadas|Troca espaços à esquerda por tabulações quando for apropriado.|  
|Cancelar tabulação das linhas selecionadas|Troca tabulações à esquerda por espaços. Se você desejar converter todos os espaços em seu arquivo para tabulações (ou todas as tabulações para espaços), você poderá usar os comandos `Edit.ConvertSpacesToTabs` e `Edit.ConvertTabsToSpaces`. Esses comandos não aparecem nos menus do Visual Studio, mas você pode chamá-los da janela de Acesso Rápido ou na janela Comando.|  
|Colocar em Maiúsculas|Alterar todos os caracteres na seleção para maiúsculos ou se não houver nenhuma seleção, altera o caractere no ponto de inserção para maiúsculo.|  
|Colocar em Minúsculas|Alterar todos os caracteres na seleção para minúsculos ou se não houver nenhuma seleção, altera o caractere no ponto de inserção para minúsculo.|  
|Mover linhas selecionadas para cima|Move a linha selecionada uma linha para cima. Atalho: ALT + SETA PARA CIMA.|
|Mover Linhas Selecionadas para Baixo|Move a linha selecionada uma linha para baixo. Atalho: ALT + SETA PARA BAIXO.|
|Validar Documento|Valida os arquivos de código JScript.|  
|Excluir Espaço em Branco Horizontal|Exclui tabulações ou espaços ao final da linha atual.|  
|Exibir Espaço em Branco|Exibe espaços como pontos elevados e tabulações como setas. O final de um arquivo é exibido como um glifo retangular. Se **Ferramentas/Opções/Editor de Texto/Todas as Linguagens/Quebra automática de linha/Mostrar glifos visíveis para quebra automática de linha** estiver selecionado, esse glifo também será exibido.|  
|Quebra automática de linha|Faz com que todas as linhas em um documento sejam visíveis na janela de código. Você pode ativar e desativar a quebra automática de linha na configuração Todas as Linguagens do Editor de Texto (**Ferramentas/Opções/Editor de Texto/Todas as Linguagens**).|  
|Remover Comentários da Seleção|Adiciona caracteres de comentários na seleção ou na linha atual.|  
|Comentar Seleção|Remove caracteres de comentários da seleção ou da linha atual.|  
|Aumentar recuo de linha|Adiciona uma tabulação (ou os espaços equivalentes) nas linhas selecionadas ou na linha atual.|  
|Diminuir recuo de linha|Remove uma tabulação (ou os espaços equivalentes) das linhas selecionadas ou da linha atual.|  
|Selecionar Marca|Em um documento que contém marcas (por exemplo, XML ou HTML), seleciona a marca.|  
|Selecionar Conteúdo da Marca|Em um documento que contém marcas (por exemplo, XML ou HTML), seleciona o conteúdo.|  

## <a name="navigate-and-find-code"></a>Navegar e localizar código  
Você pode se mover em um documento de várias maneiras diferentes. Além das operações padrão, você pode usar os botões **Navegar para Trás** (CTRL + SINAL DE SUBTRAÇÃO) e **Navegar para Frente** (CTRL + SHIFT + SINAL DE SUBTRAÇÃO) na barra de ferramentas para mover o ponto de inserção para locais anteriores ou retornar para locais mais recentes no documento ativo. Esses botões retém os últimos 20 locais do ponto de inserção.

![Botões de navegação para frente e para trás](~/ide/media/vs2017_nav_buttons.png)

O recurso Visualizador de Estrutura no editor de código exibe *linhas de guia de estrutura* – linhas verticais tracejadas que indicam a correspondência de chaves na base de código. Isso facilita ver onde os blocos lógicos começam e terminam.

![Visualizador de Estrutura](~/ide/media/vside_structure_visualizer.png)

Para desabilitar as linhas de guia de estrutura, vá até **Ferramentas**, **Opções**, **Editor de Texto**, **Geral** e limpe a caixa **Mostrar linhas de guia de estrutura**.

Você também pode usar a barra de rolagem avançada em uma janela de código para obter uma visão geral do seu código. No modo de mapa, você pode obter visualizações do código ao mover o cursor para cima e para baixo da barra de rolagem, para obter mais informações, consulte [Como controlar seu código personalizando a barra de rolagem](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

Os comandos a seguir são métodos de navegação específicos do código:  

|||  
|-|-|  
|Localizar Todas as Referências|(Menu de contexto ou SHIFT + F12): localiza todas as referências ao elemento selecionado na solução.|  
|Ir para|Contém os seguintes comandos: **Ir Para Linha** (CTRL + G): mover para o número de linha especificado no documento ativo. **Ir para Todos** (CTRL + T): mover para a linha, tipo, arquivo, membro ou símbolo especificado. **Ir para Arquivo** (CTRL + 1, CTRL + F): vá até o arquivo especificado na solução. **Ir para Tipo** (CTRL + 1, CTRL + T): vá até o tipo especificado na solução. **Ir para Membro** (CTRL + 1, CTRL + M): vá até o membro especificado na solução. **Ir para Símbolo** (CTRL + 1, CTRL + S): vá até o símbolo especificado na solução. Obtenha mais informações sobre esses comandos na seção "Localizar código usando comandos Ir Para" posteriormente neste tópico.|  
|Ir para definição|(Menu de contexto ou F12): localiza a definição do elemento selecionado.|  
|Ir Para Implementação|(Menu de contexto ou CTRL + F12): encontra o local no código onde o elemento selecionado é implementado.|
|Inspecionar Definição|(Menu de contexto ou ALT + F12): localiza a definição do elemento selecionado e a exibe em uma janela no editor de código. Para obter mais informações, consulte [How to: View and Edit Code by Using Peek Definition (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) (Como exibir e editar códigos usando Inspecionar Definição (Alt + F12)).|  
|Próximo método, Método anterior|(**Editar/Próximo método, Método anterior**) nos arquivos de código do Visual Basic, use estes comandos para mover o ponto de inserção para métodos diferentes.|  
|Realce de referência|Quando você clica em um símbolo no código-fonte, todas as instâncias desse símbolo são realçadas no documento. Os símbolos realçados podem incluir declarações e referências e muitos outros símbolos que **Localizar Todas as Referências** retornaria. Isso inclui os nomes de classes, objetos, variáveis, métodos e propriedades. No código do Visual Basic, as palavras-chave de muitas estruturas de controle também são realçadas. Para mover-se para o próximo símbolo realçado ou para o anterior, pressione CTRL + SHIFT + SETA PARA BAIXO ou CTRL + SHIFT + SETA PARA CIMA. Você pode alterar a cor do realce em **Ferramentas/Opções/Ambiente/Fontes e Cores/Referência Realçada.**|  
|Localizar informações relacionadas ao código|Você pode localizar informações sobre o código específico, como alterações e quem fez essas alterações, referências, bugs, itens de trabalho, revisões de código e status de teste de unidade ao usar o CodeLens no editor de código. O CodeLens funciona como uma exibição de alerta quando você usa o Visual Studio Enterprise com o Team Foundation Server. Consulte [Localizar alterações de código e outros históricos](../ide/find-code-changes-and-other-history-with-codelens.md).|
|Exibir Hierarquia de Chamada|(Menu de contexto ou CTRL + K, CTRL + T).|  

 Você também pode usar a **barra de navegação** (caixas suspensas na parte superior da janela de código) para localizar códigos em uma base de código. É possível escolher um tipo ou membro para ir diretamente a ele. A barra de navegação é exibida ao editar códigos no Visual Basic, C# ou base de código C++.

 ![Barra de navegação de código](~/ide/media/vside_navigation_bar.png)

 Para ocultar a barra de navegação, altere a opção **Barra de navegação** na configuração Todas as Linguagens do Editor de Texto (**Ferramentas**, **Opções**, **Editor de Texto**, **Todas as Linguagens** ou você pode alterar as configurações de linguagens individuais). Você pode navegar nas caixas suspensas da seguinte maneira:  

-   Para mudar o foco da janela de código para a barra de navegação, pressione a combinação de tecla de atalho CTRL + F2.  

-   Para retornar o foco da barra de navegação para a janela de código, pressione a tecla ESC.  

-   Para mudar o foco de um item ao outro item na barra de navegação, pressione a tecla TAB.  

-   Para selecionar o item de Barra de navegação que tem o foco e retornar ao IDE, pressione a tecla ENTER  

-   Para navegar até uma classe ou um tipo, selecione seu nome na lista suspensa à esquerda.  

-   Para navegar diretamente até um procedimento em uma classe, selecione um procedimento na lista suspensa à direita.  

 Em uma classe parcial, os membros definidos fora do arquivo de código atual podem estar desabilitados (em cinza).  

## <a name="find-code-using-go-to-commands"></a>Localizar código usando comandos Ir Para
Os comandos **Ir Para** do Visual Studio executam uma pesquisa restrita do seu código para ajudá-lo a localizar rapidamente itens especificados em arquivos de código, caminhos de arquivo e símbolos de código. Ao contrário de outras pesquisas de texto como Localizar ou Localizar nos Arquivos, o Ir Para limita sua pesquisa às áreas no qual o código real está, como em arquivos, formulários e módulos de código. Por exemplo, se você pesquisar uma cadeia de caracteres em um aplicativo Web ASP .NET usando Localizar ou Localizar nos Arquivos em toda a solução, você poderá obter várias ocorrências que incluem instâncias da cadeia de caracteres nos comentários de código. Ao utilizar um comando Ir Para, entretanto, sua pesquisa pode identificar a função que está procurando, ignorando as instâncias da cadeia de caracteres nos comentários de código.

### <a name="find-code-using-go-to"></a>Localizar código usando Ir Para

1. No Visual Studio, abra uma solução ou uma pasta.
1. No menu principal, escolha **Editar**, **Ir Para**. Uma pequena caixa de texto é exibida no canto superior do editor de código.
1. Na caixa de texto, digite o nome do elemento de código que você deseja localizar.

    ![Janela Navegar Para](~/ide/media/vside_navigatetowindow.png "Janela Navegar Para")

    Conforme você digita, os resultados são exibidos em uma lista suspensa abaixo da caixa de texto.
1. Para ir até um elemento, escolha-o na lista.


### <a name="filter-your-search"></a>Filtrar sua pesquisa

Por padrão, o item especificado é pesquisado em todos os itens de solução. No entanto, é possível limitar sua pesquisa de código para tipos de elementos específicos ao preceder os termos de pesquisa com determinados caracteres. A maneira mais fácil de abrir a caixa de diálogo Ir Para é escolher CTRL + T e, em seguida, alterar o caractere precedido para um na lista a seguir. (Como alternativa, você pode escolher as seguintes teclas de atalho para adicionar o caractere automaticamente para você.)

|Símbolo|Descrição|  
|-|-|
|Nenhum|Nenhum caractere precedido. Isso localiza o termo especificado em todas as linhas, arquivos, tipos, membros e símbolos. Atalho: CTRL + T|
|:|Vá até o número de linha especificado. Atalho: CTRL + G|
|f|Vá até o nome de arquivo especificado. Atalho: CTRL + 1, CTRL + F|
|t|Vá até o tipo especificado. Atalho: CTRL + 1, CTRL + T|
|m|Vá até o membro especificado. Atalho: CTRL + 1, CTRL + M|
|#|Vá até o símbolo especificado. Atalho: CTRL + 1, CTRL + S|

Por exemplo, para limitar sua pesquisa para somente símbolos de códigos, abra a caixa de diálogo Ir Para pressionando CTRL + T (ou CTRL +,) e, em seguida, preceda sua consulta do Ir Para com um caractere "#", ou escolha **Editar**, **Ir Para**, **Ir para o Símbolo** no menu. Procurar por `# application`, por exemplo, exibe somente símbolos de códigos que contêm a palavra "aplicativo".

É possível também alterar rapidamente o filtro de pesquisa ao escolher botões na barra de ferramentas da caixa de diálogo Ir Para. Botões que alteram os filtros estão do lado esquerdo e botões que alteram o escopo da pesquisa estão do lado direito.

![](~/ide/media/vside_navigation_toolbar.png)

Se você usar [minúsculas concatenadas](https://en.wikipedia.org/wiki/Camel_case) em seu código, será possível encontrar elementos de código de forma mais rápida, inserindo somente as letras maiúsculas do nome do elemento de código. Por exemplo, se o código tem um tipo chamado `CredentialViewModel`, é possível refinar a pesquisa ao escolher o filtro Tipo ("t") e, em seguida, inserir apenas as letras maiúsculas do nome (`CVM`) na caixa de diálogo Ir Para.

![Janela Navegar Para – pesquisando com letras maiúsculas](~/ide/media/vside_capitalsearch.png)

Esse recurso pode ser útil caso seu código tenha nomes longos.

## <a name="finding-references-in-your-codebase"></a>Localizando referências em sua base de código
Para localizar onde os elementos de código específicos são referenciados em toda a sua base de código, é possível usar o comando **Localizar Todas as Referências**. Para usar **Localizar Todas as Referências**, selecione esse comando no menu de contexto (clicando com o botão direito do mouse) do elemento que deseja localizar as referências, ou use as teclas SHIFT + F12.

Os resultados são exibidos em uma janela de ferramentas chamada  **'*{element}*' references* *, na qual *{element}* é o nome do item que está procurando. Uma barra de ferramentas na janela Referências permite que você:
- Altere o escopo da pesquisa em uma caixa de listagem suspensa. É possível optar por examinar apenas documentos alterados até a solução inteira.
- Copie o item referenciado selecionado ao selecionar o botão **Copiar**.
- Escolha os botões para ir ao local seguinte ou anterior na lista, ou escolha as teclas F8 ou SHIFT + F8.
- Remova todos os filtros nos resultados retornados, escolhendo o botão **Limpar Todos os Filtros**.
- Altere a forma que os itens retornados são agrupados ao escolher uma configuração na caixa de listagem suspensa **Agrupar por:**.
- Mantenha a janela de resultados da pesquisa atual ao escolher o botão **Manter Resultados**.
- Pesquisar cadeias de caracteres nos resultados da pesquisa ao inserir texto na caixa de texto **Pesquisar Localizar Todas as Referências**.

Também é possível passar o mouse por qualquer resultado de pesquisa para obter uma visualização do item devolvido.

![Janela de ferramentas Localizar Todas as Referências](~/ide/media/vside_findallreferences.png)

Para manter os resultados da pesquisa, selecione o botão **Manter resultados**. Ao selecionar este botão, os resultados da pesquisa atual ficam nessa janela, e novos resultados da pesquisa são exibidos em uma nova janela de ferramentas.

### <a name="navigate-to-references"></a>Navegue até referências
Na caixa de diálogo Localizar Todas as Referências, é possível usar os seguintes métodos para navegar até as referências.

- Use a tecla F8 para ir até a próxima referência ou SHIFT + F8 para ir até a referência anterior.
- Pressione a tecla ENTER em uma referência ou clique duas vezes nela para ir acessá-la no código.
- No menu de contexto de uma referência, escolha os comandos **Ir ao Local Anterior** / **Ir ao Próximo Local**.
- Use as teclas de seta para CIMA e para BAIXO (se estiverem habilitadas na caixa de diálogo Opções). Para habilitar essa funcionalidade, no menu, selecione **Ferramentas**, **Opções**, **Ambiente**, **Guias e Janelas**, **Guia Visualizar**e, em seguida, selecione as caixas **Permitir que novos arquivos sejam abertos na guia de visualização** e **Visualizar arquivos selecionados em Localizar Resultados**.

### <a name="change-reference-groupings"></a>Alterar agrupamentos de referência
Por padrão, as referências são agrupadas por projetos, depois por definição. No entanto, é possível mudar essa ordem de agrupamento, alterando a configuração na caixa de listagem suspensa **Agrupar por:** na barra de ferramentas. Por exemplo, é possível alterá-la na configuração padrão de **Definição em vez de projeto** para **Projeto em vez de definição**, assim como outras configurações.

**Definição** e **Projeto** são dois agrupamentos padrão usados, mas é possível adicionar outros ao escolher o comando **Agrupamento** no menu de contexto do item selecionado. Pode ser útil adicionar mais agrupamentos se sua solução tem muitos arquivos e caminhos.

## <a name="customize-the-editor"></a>Personalizar o Editor  
É possível compartilhar configurações do Visual Studio com outro desenvolvedor, fazer com que suas configurações estejam em conformidade com um padrão ou retornar às configurações padrão do Visual Studio usando o comando **Assistente de Importação e Exportação de Configurações** no menu **Ferramentas**. No **Assistente de Importação e Exportação de Configurações**, é possível alterar configurações gerais selecionadas ou idioma e configurações específicas do projeto.

Para definir novas teclas de atalho ou redefinir as teclas de atalho existentes, vá até **Ferramentas**, **Opções**, **Ambiente**, **Teclado**. Para obter mais informações sobre teclas de atalho, consulte [Atalhos de teclado padrão](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

Para obter mais informações sobre como personalizar o editor, consulte [Personalizando o Editor](../ide/customizing-the-editor.md). Para obter mais informações sobre as opções do editor específicas a um idioma, consulte [Usando o Ambiente de Desenvolvimento do Visual Studio para C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) e [Opções, Editor de texto, JavaScript, Formatação](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Consulte também  
 [Visual Studio IDE](../ide/visual-studio-ide.md)

