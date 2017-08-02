---
title: REPL interativo com as Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45d7c6ff-abd3-42a4-8376-0e9c8f7226d5
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
ms.openlocfilehash: d1d1030c112e5c5d27beb7b0623b0450bc3d9732
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-the-r-interactive-window"></a>Trabalhando com a janela R Interativo

As RTVS (Ferramentas do R para Visual Studio) fornecem a janela R Interativo, também conhecida como janela **REPL** (Read-Evaluate-Print-Loop), na qual você pode inserir código R e ver os resultados imediatamente. Todos os módulos, sintaxe e variáveis, bem como o IntelliSense, estão disponíveis na janela interativa.

A janela interativa também está integrada às janelas regulares do editor R. Você pode selecionar o código e pressionar Ctrl + Enter ou clicar com botão direito do mouse e selecionar **Executar em Interativo** e o código será executado linha por linha na janela interativa como se você tivesse digitado diretamente. Quando o cursor está em uma única linha na janela do editor, Ctrl + Enter envia essa linha para a janela interativa e, em seguida, move o cursor para a próxima linha. Dessa forma, basta pressionar Ctrl + Enter várias vezes para percorrer o código.

Para experimentar, você pode seguir o passo a passo [Introdução ao R](getting-started-with-r.md), bem como as seções a seguir:

- [Visão geral da janela interativa](#overview-of-the-interactive-window)
- [Espaços de trabalho e sessões](#workspaces-and-sessions)
- [Diretório de trabalho](#working-directory)
- [Histórico](#history)

Os [Trechos de código](code-snippets.md) também funcionam na janela interativa como nas janelas do editor de R.

## <a name="overview-of-the-interactive-window"></a>Visão geral da janela interativa

Digitar um código R válido e pressionar Enter no final da linha executará o código nessa linha:

```
> 3 + 3
[1] 6
```

Pressionar Enter em qualquer lugar em uma única linha de entrada também executará essa linha.

Todas as entradas e saídas anteriores da REPL são somente leitura e não podem ser alteradas. No entanto, você pode selecionar e copiar o texto da janela a qualquer momento e também colá-lo. O código colado será executado como se fosse inserido linha por linha.

Ou seja, quando você começar a digitar uma instrução e pressionar Enter, as RTVS saberam quando a instrução deve ser continuada e entrarão no modo de várias linha com um + prompt no recuo apropriado à esquerda. As RTVS também preencherão as chaves, os colchetes e os parênteses:

![Entrada de instrução de várias linhas na janela interativa](~/rtvs/media/repl-multiline-entry.png)

Nesse modo de várias linhas, a tecla Enter executa o bloco de código somente quando posicionada no final do bloco, caso contrário, insere uma nova linha. No entanto, você pode pressionar Ctrl + Enter em qualquer posição para executar esse bloco de código imediatamente.

### <a name="toolbar-commands"></a>Comandos da barra de ferramentas

A janela interativa com sua barra de ferramentas é mostrada abaixo:

![Janela interativa com barra de ferramentas](~/rtvs/media/repl-window.png)

Os comandos da barra de ferramentas são os mostrados a seguir. A maioria deles tem equivalentes de teclado e também está disponível nos menus **Ferramentas do R > Sessão** e **Ferramentas do R > Diretório de Trabalho** (ou conforme observado):

| Botão | Comando | Combinação de teclas | Descrição | 
| --- | --- | --- | --- |
| ![Botão Redefinir](~/rtvs/media/repl-toolbar-01-reset.png) | Redefinir | Ctrl+Shift+F10 | Redefine a sessão de janela interativa, limpando todas as variáveis e o histórico. |
| ![Botão Limpar](~/rtvs/media/repl-toolbar-02-clear.png) | Clear | Ctrl+L | Limpa a saída mostrada na janela interativa. não afeta as variáveis de sessão nem o histórico. |
| ![Botões Histórico](~/rtvs/media/repl-toolbar-03-history.png) | Comando Histórico anterior<br/>Comando Próximo histórico | Para cima, para baixo<br/>ALT + seta para cima, Alt + seta para baixo | Percorre o histórico, com alguns comportamentos de blocos de código de várias linhas. Consulte [Histórico](#history). |
| ![Botão Carregar espaço de trabalho](~/rtvs/media/repl-toolbar-04-load-workspace.png) | Carregar espaço de trabalho | N/D | Carrega um espaço de trabalho anterior salvo (consulte [Espaços de trabalho e sessões](#workspaces-and-sessions). |
| ![Botão Salvar espaço de trabalho como](~/rtvs/media/repl-toolbar-05-save-workspace-as.png)| Salvar espaço de trabalho | N/D | Salva o estado atual da sessão como um espaço de trabalho (consulte [Espaços de trabalho e sessões](#workspaces-and-sessions). |
| ![Botão Script R de origem](~/rtvs/media/repl-toolbar-06-source-r-script.png) | Script R de origem | Ctrl+Shift+S | Chama `source` com o script R atualmente ativo no editor do Visual Studio, que executa o código.  Esse botão só aparece quando um arquivo R é aberto no editor do Visual Studio. | 
| ![Botão Script R de origem com eco](~/rtvs/media/repl-toolbar-07-source-r-script-with-echo.png) | Script R de Origem com Eco | Ctrl+Shift+Enter | Igual ao Script R de Origem, mas exibe o conteúdo do script na janela interativa. | 
| ![Botão Interromper R](~/rtvs/media/repl-toolbar-08-interrupt-r.png)| Interromper R | Esc | Interrompe qualquer código em execução na janela interativa, como o loop `while` na captura de tela acima. |
| ![Botão Anexar depurador](~/rtvs/media/repl-toolbar-09b-attach-debugger.png)| Anexar depurador | N/D | Também disponível usando o comando **Depurar > Anexar a R Interativo**. | 
| ![Botão Definir diretório de trabalho para o local do arquivo de origem](~/rtvs/media/repl-toolbar-10-set-working-directory-source.png)| Definir diretório de trabalho para o local do arquivo de origem | Ctrl+Shift+E | Define o diretório de trabalho para o último arquivo de origem carregado na janela interativa (usando `source`). Consulte [Diretório de trabalho](#working-directory). |
| ![Botão Definir diretório de trabalho para o local do projeto](~/rtvs/media/repl-toolbar-11-set-working-directory-to-project.png) | Definir diretório de trabalho para o local do projeto | Ctrl+Shift+P | Define o diretório de trabalho para a raiz do projeto carregado atualmente no Visual Studio. Consulte [Diretório de trabalho](#working-directory). |
| (Campo de texto) | Selecionar Diretório de Trabalho | N/D | Campo de entrada direta para o diretório de trabalho. Consulte [Diretório de trabalho](#working-directory). |


## <a name="workspaces-and-sessions"></a>Espaços de trabalho e sessões

Executar código na janela interativa cria um contexto na sessão atual, composto de variáveis globais, definições de função, cargas de biblioteca e assim por diante. Esse contexto é chamado coletivamente de *espaço de trabalho* e você pode salvar e carregar espaços de trabalho a qualquer momento. 

Selecionar o botão **Salvar espaço de trabalho como** ou usar o comando **Ferramentas do R > Sessão > Salvar espaço de trabalho como...** solicitará um local e nome de arquivo (a extensão padrão é `.RData`).
Para salvar um Espaço de trabalho usando um nome de arquivo específico (o padrão é `.RData`), clique no botão Salvar espaço de trabalho na REPL:

Para recarregar um espaço de trabalho salvo anteriormente, selecione o botão **Carregar espaço de trabalho** ou use **Ferramentas do R > Sessão > Carregar espaço de trabalho...** e navegue até o arquivo do espaço de trabalho.

O botão **Redefinir** ou **Ferramentas do R > Sessão > Redefinir** limpa o contexto da sessão. Observe que se você estiver usando uma sessão remota, isso também excluirá o perfil do usuário no computador remoto para limpar todos os arquivos armazenados ali. (Consulte [Espaços de trabalho](workspaces.md#directories-on-local-and-remote-computers).)


## <a name="working-directory"></a>Diretório de trabalho

Normalmente, os desenvolvedores desejam alterar seu diretório de trabalho enquanto estão em uma sessão interativa. Vários comandos, disponíveis na barra de ferramentas, no menu **Ferramentas do R > Diretório de trabalho** e no menu de contexto do projeto, permitem que você configure facilmente um diretório de trabalho para o local de um arquivo de origem, o local do projeto ou qualquer outro local. Isso ajuda a evitar a digitação de nomes de caminho completos ou de nomes de caminho relativos longos ao fazer referência a arquivos.

 
## <a name="history"></a>Histórico

Cada linha que você insere na janela interativa, incluindo as linhas enviadas de um editor, são mantidas no histórico da REPL. Você pode navegar pelo histórico com as teclas de seta Para Cima e Para Baixo, como provavelmente já está acostumado na linha de comando.

Uma diferença é que, se você começar a digitar na linha atual e, em seguida, pressionar Para Cima, essa linha atual será preservada no histórico, mesmo que ela ainda não tenha sido executada.

O histórico na janela interativa também funciona de forma inteligente com instruções de outro bloco de código que abrangem linhas. Ao percorrer o histórico com as teclas de seta Para Cima e Para Baixo, os blocos de código de várias linhas são recuperados como um todo e mostrados como a entrada atual. Neste ponto, as teclas de seta navegarão por esse bloco de código linha por linha, até a parte superior ou inferior seja atingida. Na parte superior do bloco de código, a seta para cima recupera o item anterior no histórico; na linha inferior, a seta para baixo recupera o próximo item.

Isso acomoda o caso comum de executar novamente o último item no histórico com a combinação de pressionamento de tecla de seta Para Cima e Enter, permitindo naturalmente a edição de um bloco de código de várias linhas ao pressionar a seta Para Cima para navegar nele.

Para evitar a navegação em blocos de código de várias linhas, use os botões da barra de ferramentas ou use Alt + seta para cima e Alt + seta para baixo e todos esses blocos serão tratados como uma única linha.

A maneira mais fácil de experimentar isso, é simplesmente você mesmo usar a janela interativa. O código a seguir fornece várias instruções adequadas de linha única e de várias linhas. No entanto, copie e cole cada instrução individualmente, para criar o histórico apropriado. (A mesma coisa pode ser feita colando o código em um arquivo de código separado e, em seguida, enviando as linhas para a janela interativa com Ctrl + Enter).

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```
