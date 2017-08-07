---
title: "Gerenciador de Variáveis nas Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/30/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c669434-40d8-4970-92cc-502a98c8b5ab
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 92396808161886cf3b15f7e8e0ab23a0a35e26b9
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="variable-explorer"></a>Gerenciador de Variáveis

A janela **Gerenciador de Variáveis**, aberta usando **Ferramentas do R > Janelas > Gerenciador de Variáveis** (ou Ctrl + 8 se você já usou **Ferramentas do R > Configurações da Ciência de Dados**), mostra todas as variáveis em um determinado escopo na sessão atual do R. Por exemplo, se abrir o Gerenciador de Variáveis e inserir as seguintes linhas na [janela interativa](interactive-repl.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```
 
A janela Gerenciador de Variáveis aparecerá da seguinte maneira:

![Janela do Gerenciador de Variáveis no Visual Studio](media/variable-explorer-window.png)

Se você tiver um quadro de dados R mais complexo definido na sessão, será possível navegar nos dados. Por exemplo, após a execução de `cars <- mtcars`, você pode navegar pelo conjunto de dados expandindo os diferentes nós no Gerenciador de Variáveis:
 
![Exibição expandida do Gerenciador de Variáveis](media/variable-explorer-expanded-results.png)
 
Para excluir variáveis, clique com o botão direito do mouse e selecione **Excluir** ou selecione a variável e pressione a tecla Excluir.

Você também pode procurar uma observação em um quadro de dados usando a pesquisa incremental. Primeiro, expanda os nós no quadro de dados que deseja pesquisar e insira os termos de pesquisa na caixa de pesquisa.

## <a name="details-table-view"></a>Exibição de detalhes (tabela)

Como os dados costumam ser tabulares, você pode exibir qualquer tipo de dados complexo como uma tabela separada, selecionando o ícone de lupa ou clicando com o botão direito do mouse e selecionando **Mostrar Detalhes**. 

![Exibição de tabela do Gerenciador de Variáveis](media/variable-explorer-table-view.png)

Clicar em um título de coluna classifica os dados pela coluna (alternando entre crescente e decrescente). Manter pressionada a tecla Shift e clicar em colunas adicionais também adiciona essas colunas à classificação. Clicar em uma coluna sem Shift retorna para a classificação de uma única coluna.

A sequência em que você clica nos títulos de coluna determina a ordem na qual a classificação é executada. Por exemplo, Shift + clique na coluna **cyl**, em seguida, Shift + clique duplo na coluna **mpg**, classifica a lista em cilindros crescentes e milhas por galão decrescentes:

![Exibição de tabela de classificação de dados por duas colunas.](media/variable-explorer-table-view-sorting.png)

Como o Gerenciador de Variáveis e as exibições de tabela estão em janelas separadas do Visual Studio, você pode organizá-las para trabalhar lado a lado. Consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) para obter instruções gerais.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Abrir no Excel (ou em outro aplicativo compatível com CSV)

Para manipulação adicional e análise, geralmente é útil exportar as variáveis de sessão para CSV. A exportação é feita com o ícone pequeno do Excel (![Ícone de exportação do Excel](media/variable-explorer-excel-icon.png)) ao lado de cada nó no Gerenciador de Variáveis ou clicando com o botão direito do mouse em um item e selecionando **Abrir em aplicativo CSV**. Selecionar o ícone grava os dados em um novo arquivo CSV na pasta `%userprofile%\Documents\RTVS_CSV_Exports` e, em seguida, inicia esse arquivo, que abre em qualquer outro aplicativo que esteja associado à extensão `.csv`.

## <a name="scopes"></a>Escopos

Por padrão o Gerenciador de Variáveis abrirá o escopo global. Você pode mudar para um escopo de pacote, selecionando um pacote no menu suspenso na parte superior da janela.

![Gerenciador de Variáveis mostrando um escopo de pacote](media/variable-explorer-package-scopes.png)

Você também pode mudar para um escopo de função ao ser interrompido um ponto de interrupção no depurador (observe que o Gerenciador de Variáveis não muda automaticamente para o escopo da função do código que está sendo depurado):

![Gerenciador de Variáveis mostrando um quadro de dados durante a depuração](media/variable-explorer-as-locals-window.png)

O Gerenciador de Variáveis altera o escopo da função automaticamente conforme você percorre o código no depurador, como mostrar variáveis locais em uma função.


## <a name="importing-data-into-variable-explorer"></a>Importando dados para o Gerenciador de Variáveis

Dois comandos na barra de ferramentas do Gerenciador de Variáveis, que também estão disponíveis no menu **Ferramentas do R > Dados**, importam conjuntos de dados CSV externos para a sessão do R: **Importar conjunto de dados na sessão do R de URL da Web** e **Importar conjunto de dados na sessão do R de arquivo de texto**. 

Depois de identificar o arquivo CSV a ser importado, o Visual Studio exibe uma caixa de diálogo **Importar Conjunto de Dados**, na qual há opções para controlar como esse arquivo de dados é analisado (ou seja, o que é o separador de campo e como lidar com aspas). Você também pode ver uma versão prévia do quadro de dados importado e do arquivo de dados original:

![Caixa de diálogo Importar conjunto de dados](media/variable-explorer-import-dataset-dialog.png)

