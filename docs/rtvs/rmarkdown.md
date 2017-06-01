---
title: R Markdown com Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
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
ms.openlocfilehash: 972abfcfda570d66b1b15b25b16e68157fc73b81
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---

# <a name="creating-r-markdown-documents"></a>Criando documentos R Markdown

R Markdown (consulte [rmarkdown.rstudio.com](https://rmarkdown.rstudio.com/)) de um formato de documento que transforma a análise em R em painéis, relatórios, apresentações e documentos de alta qualidade.

As Ferramentas do R para Visual Studio fornecem um modelo de item R Markdown, suporte a editor (incluindo IntelliSense para código R dentro do editor) e recursos de geração de arquivo.

Para usar o R Markdown:

1. Feche o Visual Studio.
1. (Apenas uma vez) Instalar o pandoc de [pandoc.org](http://pandoc.org/installing.html).
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

