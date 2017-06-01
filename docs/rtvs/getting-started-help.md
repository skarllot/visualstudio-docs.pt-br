---
title: Janela da Ajuda nas Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
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
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>Ajuda nas Ferramentas do R para Visual Studio

A ajuda do R está integrada diretamente na janela interativa no Visual Studio. Sempre que você usar o comando `?`, como `?mtcars`, a ajuda da documentação do R aparecerá em uma janela do Visual Studio:

![janela da Ajuda no Visual Studio](media/help-window.png)

> [!Tip]
> A janela da Ajuda, como todas as outras no Visual Studio, pode ser organizada e encaixada conforme o desejado. Consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Você também pode abrir os resultados da Ajuda em um navegador, selecionando o menu **Ferramentas do R > Opções** e definindo a propriedade **Navegador da Ajuda do R** como `External`. Consulte [Opções](options.md).

Para pesquisar a ajuda, use o comando `??` com o termo de pesquisa entre aspas se ele incluir espaços:

```R
??"Motor Trend"
```

![Resultados da pesquisa da ajuda](media/help-search1.png)

A janela da Ajuda também tem um campo de entrada de pesquisa por meio do qual você pode realizar mais pesquisas diretamente na documentação do R:

![Resultados da pesquisa da ajuda usando o campo de entrada](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Pesquisa da ajuda integrada

Como os desenvolvedores geralmente pesquisam a documentação do R para obter ajuda com nomes de função, conjuntos de dados e outros elementos, as Ferramentas do R para Visual Studio simplificam o processo, integrando as pesquisas da ajuda diretamente no editor e na janela interativa.

- Pressionar F1 durante uma operação de preenchimento automático produz uma lista de resultados da ajuda que correspondem à subcadeia de caracteres.
- Clique com o botão direito do mouse em um termo de pesquisa (como uma função) e selecione o comando **Ajuda sobre** ou simplesmente pressione F1 para abrir a ajuda para essa função. Você também pode invocar **Ajuda sobre** para qualquer seleção.

    ![Invocando a ajuda por meio do menu de contexto acionado com um clique no botão direito do mouse](media/help-right-click.png)

> [!Tip]
> Para abrir a ajuda integrada em um navegador, selecione **Ferramentas do R > Opções** e defina **Navegador da Web F1** para `External`. Consulte [Opções](options.md).

## <a name="integrated-stackoverflow-search"></a>Pesquisa integrada do StackOverflow

Além de pesquisar na documentação do R, os desenvolvedores geralmente pesquisam no StackOverflow enquanto escrevem o código. As RTVS simplificam o processo. Quando você clica com o botão direito do mouse em um termo ou em uma seleção e seleciona o comando **Pesquisar na Web** ou simplesmente pressiona Ctrl + F1, uma janela do Visual Studio (ou um navegador, se você tiver alterado a opção **Navegador da Web F1**) será aberta contendo os resultados da pesquisa do termo que tem como escopo o StackOverflow por padrão:

![Resultados da pesquisa da Web no Visual Studio](media/help-web-search-results.png)

Você pode alterar a cadeia de caracteres acrescentada, `R site:stackoverflow`, por meio da opção **Ferramentas do R > Opções > Cadeia de Pesquisa da Web F1**:

![Alterando a opção de cadeia de pesquisa da Web F1](media/options-dialog.png)
