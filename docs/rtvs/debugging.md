---
title: Depurando com as Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: e4b8d7fb27407bf8ef4463524e9da66bac591ff4
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="debugging-r-in-visual-studio"></a>Depurando R no Visual Studio

As RTVS (Ferramentas do R para Visual Studio) se integram à experiência de depuração completa do Visual Studio (consulte [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)). Esse suporte inclui pontos de interrupção, a anexação a processos em execução, a inspeção e a observação de varáveis e a inspeção da pilha de chamadas. Portanto, este tópico explora os aspectos de depuração que são exclusivos para R e RTVS.

A inicialização do depurador para o arquivo de inicialização R em um projeto R é igual a para outros tipos de projeto: use **Depurar > Iniciar Depuração**, a tecla F5 ou o **Arquivo de inicialização de origem** na barra de ferramentas de depuração mostrada abaixo: 

![Botão Iniciar depurador para R](media/debugger-start-button.png)

Para alterar o arquivo de inicialização, clique com o botão direito do mouse em um arquivo no Gerenciador de Soluções e selecione **Definir Como Script R de Inicialização**.

Em todos os casos, iniciar o depurador "origina" o arquivo na janela interativa, o que significa carregá-lo e executá-lo lá como mostrado na saída da janela interativa:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Observe que a função `rtvs::debug_source` é usada para o script de origem. Essa função é necessária porque as RTVS precisam modificar o código na preparação para a depuração. Ao usar qualquer comando de fornecimento de RTVS e um depurador estiver anexado, o Visual Studio automaticamente usará `rtvs::debug_source`.

Você também pode anexar manualmente o depurador diretamente por meio da janela interativa usando o comando **Ferramentas do R > Sessão > Anexar Depurador**, o comando **Depurar > Anexar a R Interativo** ou o comando **Anexar Depurador** na barra de ferramentas da janela interativa. Depois de fazer isso, será sua responsabilidade originar os arquivos que deseja depurar. Se você quiser originar os arquivos manualmente, certifique-se de usar `rtvs::debug_source` e não o comando `source` regular no R.

Essa conexão entre o depurador e a janela interativa facilita ações como chamar (e depurar) uma função com valores de parâmetros diferentes. Por exemplo, suponha que você tenha a seguinte função em um arquivo originado (o que significa que ela foi carregada na sessão):

```R
add <- function(x, y) {
    return(x + y)
}
```

Em seguida você define um ponto de interrupção na instrução `return`. Agora, na janela interativa, inserir `add(4,5)` interrompe o depurador no seu ponto de interrupção.


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

