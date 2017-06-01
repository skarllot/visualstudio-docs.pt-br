---
title: "Opções das Ferramentas do R no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- VS.ToolsOptionsPages.R_Tools.%23150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 9b680c73d54c9809e3f4c46dc2841f1f320e4af9
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="r-tools-for-visual-studio-options"></a>Opções das Ferramentas do R para Visual Studio
 
As configurações são acessadas por meio do menu **Ferramentas do R > Opções** ou de **Ferramentas > Opções** e rolando até **Ferramentas do R**:
 
  ![Caixa de diálogo de opções para Ferramentas de R](media/options-dialog.png)

As seções a seguir descrevem as diferentes opções disponíveis nesta página...

> [!Note]
> Ao acessar as opções pelo menu geral **Ferramentas > Opções**, você precisará selecionar a caixa **Mostrar todas as configurações** na parte inferior, para que a página **Ferramentas do R** apareça.

<a name="data-scientist-layout"</a>

Também há um item de menu especial **Ferramentas do R > Configurações da ciência de dados** que configura o IDE do Visual Studio com um layout que é otimizado para as necessidades dos cientistas de dados. Especificamente, essa opção abre as janelas [Interativo](interactive-repl.md), [Gerenciador de Variáveis](variable-explorer.md) e [Espaços de trabalho](workspaces.md):

![Layout da janela do cientista de dados no Visual Studio](media/installation-data-scientist-layout-result.png)

> [!Important]        
> Para reverter posteriormente para outras configurações do Visual Studio, primeiro use o comando **Ferramentas > Importar e Exportar Configurações**, selecionando **Exportar configurações de ambiente selecionadas** e especificar um nome do arquivo. Para restaurar essas configurações, use o mesmo comando e selecione **Importar configurações de ambiente selecionadas**. Você também poderá usar os mesmos comandos se você alterar o layout do cientista de dados e quiser retornar a ele, em vez de usar o comando **Configurações da ciência de dados** diretamente.

## <a name="debugging"></a>Depuração

Essas opções controlam como os valores são manipulados no [Gerenciador de Variáveis](variable-explorer.md) e nas janelas da ferramenta Depurador como Inspeção e Locais (consulte [Depuração](debugging.md).

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Avaliar associações ativas | `True` | Quando `True`, garante que você sempre veja o valor mais atualizado ao inspecionar variáveis e propriedades. O risco é que avaliar as expressões pode causar efeitos colaterais, dependendo de como elas foram implementados. |
| Mostrar variáveis prefixadas com ponto | `False` | Especifica se as variáveis prefixadas com `.` são mostradas. |

## <a name="general"></a>Geral

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Verificação de pesquisa/notícias | `Once a week` | Especifica com que frequência as Ferramentas do R devem verificar com o servidor se há atualizações de notícias e pesquisa. | 

## <a name="help"></a>Ajuda

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Navegador da Web F1 | `Internal` | Controla como a ajuda é exibida ao procurar por um termo usando Ctrl + F1. Quando definido como `Internal`, a ajuda é renderizada dentro de uma janela de ferramentas no Visual Studio. Quando definido como `External`, a ajuda é exibida no navegador da Web padrão. | 
| Cadeia de pesquisa da Web F1 | `R site:stackoverflow.com` | Controla como os termos de pesquisa são passados para o mecanismo de pesquisa ao pressionar Ctrl + F1 em um termo no editor. Por padrão a cadeia de caracteres é `R site:stackoverflow.com`, que acrescenta `R` ao termo de pesquisa. O `site:stackoverflow.com` é uma diretiva que solicita ao mecanismo de pesquisa a inclusão de pesquisar em páginas no escopo do domínio do `stackoverflow.com`. | 
| Navegador da Ajuda do R | `Automatic` | Controla como a ajuda é exibida ao pesquisar a documentação do R usando F1, `?` ou `??`. Quando definido como `Automatic`, a ajuda é renderizada na janela apropriada. Por exemplo, a ajuda em HTML aparece em uma janela de ferramentas do Visual Studio, enquanto PDFs aparecem no programa de PDF padrão. Quando definido como `External`, a ajuda é renderizada no navegador da Web padrão. |

## <a name="history"></a>Histórico

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Sempre salvar histórico | `True` | Controla se as RTVS gravam o histórico de comandos em um arquivo `.RHistory` no diretório de trabalho sempre que o projeto é fechado. Observe que isso acontecerá mesmo se você não salvar seu projeto antes de sair. |
| Redefinir filtro de pesquisa | `True` | Determina se a janela Histórico pode filtrar o histórico de comandos para mostrar somente os comandos que correspondem à subcadeia de caracteres em relação ao termo do filtro na caixa de diálogo Histórico do R. Essa configuração determina se o filtro de pesquisa de Histórico é redefinido sempre que você executa um novo comando ou alterna para um novo projeto, o que disparará a carga de um arquivo `.RHistory` diferente. A configuração padrão de `True` minimiza a surpresa quando você executa um comando com um conjunto de filtros e percebe que o comando que acabou de ser executado não apareceu no histórico. |
| Usar seleção de várias linhas | `True` | Especifica se é possível selecionar uma instrução de várias linhas no Histórico com um único clique. Também permite a navegação com setas para cima/para baixo nas janelas interativas por instruções e não por linhas. |

## <a name="html"></a>HTML

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Navegador de páginas HTML | `External` | Determina onde o conteúdo, como um gráfico `ggvis` ou um aplicativo `shiny`, é renderizado. `Internal` mostra a saída HTML dentro de uma janela de ferramentas no Visual Studio; `External` exibe a saída HTML no navegador padrão. | 

## <a name="logging"></a>Registrando em log

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Eventos de log | `Normal` | Controla o nível de detalhes do registro em log usado para diagnóstico das RTVS. A configuração padrão de `Normal` cria um arquivo de log em seu diretório `TEMP`. Quando definido como `Traffic`, as RTVS registram todos os comandos e as respostas em sua sessão. Esses arquivos de log nunca saem do computador, mas podem ser úteis para diagnosticar problemas nas RTVS. |

## <a name="markdown"></a>Markdown

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Navegador da visualização de markdown | `External` | Determina onde a saída HTML RMarkdown é exibida. `Internal` mostra o documento HTML RMarkdown dentro de uma janela de ferramentas no Visual Studio; `External` exibe o HTML RMarkdown usando o navegador padrão. | 

## <a name="r-engine"></a>Mecanismo do R

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Página de código | `(OS Default)` | Define a página de código (localidade) para R. Por padrão, usa a localidade subjacente do sistema operacional. | 
| Espelho CRAN | `(Use .Rprofile)` | Define o espelho CRAN padrão para instalações de pacote. A configuração padrão de `Use .Rprofile` respeita as configurações de Espelho CRAN no arquivo `.RProfile`. Você pode substituí-la selecionando um dos espelhos CRAN na lista suspensa. |
| Diretório de trabalho | pasta específica do usuário | Define o diretório de trabalho atual, que normalmente é definido sempre que um projeto é aberto. |

## <a name="workspace"></a>Espaço de trabalho

| Opção | Valor padrão | Descrição | 
| --- | --- | --- |
| Carregar espaço de trabalho quando o projeto é aberto | `No` | Definir como `Yes` permite carregar dados da sessão do arquivo `.RData` no ambiente global quando o projeto é aberto. |
| Prompt para salvar espaço de trabalho ao reiniciar | `Yes` | Definir como `No` desabilita o prompt para salvar o espaço de trabalho ao clicar no botão Redefinir na janela interativa. |
| Salvar espaço de trabalho quando o projeto é fechado | `No` | Definir como `Yes` permite salvar o ambiente global no arquivo `.RData` quando o projeto é fechado. |
| Mostrar caixa de diálogo de confirmação antes de alternar espaços de trabalho | `Yes` | Definir como `No` desabilita o prompt de confirmação do usuário ao alternar entre espaços de trabalho diferentes. Consulte [alternando entre espaços de trabalho](workspaces.md#switching-between-workspaces) |
 
