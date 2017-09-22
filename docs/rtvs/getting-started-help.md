---
title: Janela da Ajuda nas Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 2542682ecab54235a236a93c9906185547017c4c
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="help-in-r-tools-for-visual-studio"></a>Ajuda nas Ferramentas do R para Visual Studio

A ajuda do R está integrada diretamente na janela interativa no Visual Studio. Sempre que você usar o comando `?`, como `?mtcars`, a ajuda da documentação do R aparecerá em uma janela do Visual Studio:

![janela da Ajuda no Visual Studio](media/help-window.png)

> [!Tip]
> A janela da Ajuda, como todas as outras no Visual Studio, pode ser organizada e encaixada conforme o desejado. Consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Para abrir os resultados da ajuda em um navegador, selecione o menu **Ferramentas do R > Opções** e defina a propriedade **Navegador da Ajuda do R** como `External`. Consulte [Opções](options.md).

Para pesquisar a ajuda, use o comando `??` seguido por um termo de pesquisa. Use aspas se o termo de pesquisa contiver espaços:

```R
??"Motor Trend"
```

![Resultados da pesquisa da ajuda](media/help-search1.png)

A janela da Ajuda também tem um campo de entrada de pesquisa por meio do qual você pode realizar mais pesquisas diretamente na documentação do R:

![Resultados da pesquisa da ajuda usando o campo de entrada](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Pesquisa da ajuda integrada

Os desenvolvedores geralmente pesquisam a documentação do R para obter ajuda sobre nomes de função, conjuntos de dados e outros elementos. As RTVS (Ferramentas do R para Visual Studio) simplificam o processo integrando as pesquisas de ajuda às janelas de editor e interativa.

- Pressionar F1 durante uma operação de preenchimento automático produz uma lista de resultados da ajuda que correspondem à subcadeia de caracteres.
- Clicar com o botão direito do mouse em um termo de pesquisa (como uma função) e selecionar o comando **Ajuda sobre** abre a ajuda para essa função. Você também pode invocar **Ajuda sobre** para qualquer seleção.

    ![Invocando a ajuda por meio do menu de contexto acionado com um clique no botão direito do mouse](media/help-right-click.png)

> [!Tip]
> Para abrir a ajuda integrada em um navegador, selecione **Ferramentas do R > Opções** e defina **Navegador da Web F1** para `External`. Consulte [Opções](options.md).

## <a name="integrated-stackoverflow-search"></a>Pesquisa integrada do StackOverflow

Além de pesquisar na documentação do R, os desenvolvedores geralmente pesquisam no StackOverflow enquanto escrevem o código. As RTVS simplificam o processo. Clique com o botão direito do mouse em um termo ou em uma seleção, selecione o comando **Pesquisar na Web por** (Ctrl+F1) e o Visual Studio abre uma janela com os resultados da pesquisa com o escopo para o StackOverflow:

![Resultados da pesquisa da Web no Visual Studio](media/help-web-search-results.png)

Você pode alterar a cadeia de caracteres de escopo acrescentada, `R site:stackoverflow`, por meio da opção **Ferramentas do R > Opções > Cadeia de pesquisa da Web F1**:

![Alterando a opção de cadeia de pesquisa da Web F1](media/options-dialog.png)

Se você preferir exibir os resultados em um navegador, altere a opção **Navegador da Web F1** conforme descrito em [Opções](options.md).
