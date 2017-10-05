---
title: R Markdown com Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b29ae0240a29616edcdf2ae0dced7a9fca0f9584
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-markdown-documents"></a>Criando documentos R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) é um formato de documento que transforma a análise em R em painéis, relatórios, apresentações e documentos de alta qualidade.

As RTVS (Ferramentas do R para Visual Studio) fornecem um modelo de item R Markdown, suporte a editor (incluindo IntelliSense para código R dentro do editor) e recursos de geração de arquivo.

Para usar o R Markdown:

1. Feche o Visual Studio.
1. (Apenas uma vez) Instalar o `pandoc` do [pandoc.org](http://pandoc.org/installing.html).
1. Reinicie o Visual Studio, que deve captar a instalação do pandoc.
1. Instale os pacotes `knitr` e `rmarkdown`, o que pode ser feito na [janela interativa](interactive-repl.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Crie um novo arquivo R Markdown usando o comando de menu **Arquivo > Novo** e selecionando **R Markdown** na lista ou clicando com o botão direito do mouse no seu projeto no Gerenciador de Soluções e selecionando **Adicionar R Markdown** (ou **Adicionar > Novo Item...** e selecionando **R Markdown** na lista).

1. O conteúdo padrão do novo arquivo é o seguinte:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---
    
    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
    
    ```{r}
    summary(cars)
    ```
    
    You can also embed plots, for example:
    
    ```{r, echo=FALSE}
    plot(cars)
    ```
    
    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
    
    ~~~

1. A qualquer momento durante a edição, clique com botão direito do mouse no editor e selecione **Visualizar**, que tem opções para HTML, PDF e Microsoft Word. Nessa visualização é possível salvar o arquivo de acordo com o formato escolhido.

