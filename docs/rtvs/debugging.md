---
title: Depurando com as Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
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
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>Depurando R no Visual Studio

As RTVS (Ferramentas do R para Visual Studio) integram-se à experiência de depuração completa do Visual Studio (consulte [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md), incluindo pontos de interrupção, anexando a processos em execução, inspecionando e verificando variáveis, inspecionando a pilha de chamadas e assim por diante. Portanto, este tópico explora os aspectos de depuração que são exclusivos para R e RTVS.

Iniciar o depurador para um o arquivo de inicialização R em um projeto R é o mesmo que para outros tipos de projeto: use **Depurar > Iniciar Depuração**, a tecla F5 ou o **Arquivo de inicialização de origem** na barra de ferramentas de depuração mostrada abaixo. Para alterar o arquivo de inicialização, clique com o botão direito do mouse em um arquivo no Gerenciador de Soluções e selecione **Definir Como Script R de Inicialização**.

![Botão Iniciar depurador para R](media/debugger-start-button.png)

Em todos os casos, iniciar o depurador "origina" o arquivo na janela interativa, o que significa carregá-lo e executá-lo lá. Quando você iniciar a depuração, na verdade, você verá uma saída como esta na janela interativa:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Você observará que estamos usando a função `rtvs::debug_source` para originar o script. Isso é necessário porque as RTVS precisam modificar o código em preparação para a depuração. Se você estiver usando um dos comandos das RTVS (por exemplo, clicando com o botão direito do mouse em um arquivo no Gerenciador de Soluções e executando o comando **Originar arquivos selecionados**), a chamada será redirecionada automaticamente para `rtvs::debug_source` se o depurador estiver anexado.

Você também pode anexar manualmente o depurador diretamente por meio da janela interativa usando o comando **Ferramentas do R > Sessão > Anexar Depurador**, o comando **Depurar > Anexar a R Interativo** ou o comando **Anexar Depurador** na barra de ferramentas da janela interativa. Depois de fazer isso, será sua responsabilidade originar os arquivos que deseja depurar. Se você quiser originar os arquivos manualmente, use `rtvs::debug_source` e não o comando `source` normal em R. Você verá que isso funciona em _alguns_ casos, mas não podemos garantir que a depuração funcionará em todos os casos, a menos que você use o comando `rtvs::debug_source`.

Essa conexão entre o depurador e a janela interativa facilita ações como chamar (e depurar) uma função com valores de parâmetros diferentes. Por exemplo, suponha que você tenha uma função semelhante à seguinte em um arquivo originado (o que significa que ele foi carregado na sessão):

```R
add <- function(x, y) {
    return(x + y)
}
```

Em seguida você define um ponto de interrupção na instrução `return`. Agora, na janela interativa, se você digitar `add(4,5)`, você verá que o depurador é interrompido no ponto de interrupção.


## <a name="environment-browser-in-the-interactive-window"></a>Navegador de ambiente na janela interativa

Quando você for interrompido no depurador, você também será interrompido no prompt de Navegador de Ambiente na [janela interativa](interactive-repl.md). O prompt será exibido como `Browse[n]>`, em que n é um número.

O Navegador de Ambiente dá suporte a uma série de comandos especiais:

| Comando | Descrição | 
| --- | --- |
| n | próxima: executa a próxima instrução no arquivo de código (o mesmo que avançar). |
| s | intervir: executa a próxima instrução no arquivo de código, executando um escopo de função quando a próxima instrução é uma chamada de função. | 
| f | concluir: executa o restante do escopo da função atual e retorna ao chamador (o mesmo que sair). |
| c, cont | continuar: executa o programa até o próximo ponto de interrupção. | 
| Q | encerra: termina a sessão de depuração. |
| onde | mostrar pilha: exibe a pilha de chamadas na janela interativa. |
| help | mostrar ajuda: exibe os comandos disponíveis na janela interativa. |
| &lt;expr&gt; | avaliar a expressão em *expr*. |

![Navegador de Ambiente na janela interativa](media/debugger-environment-browser.png)

