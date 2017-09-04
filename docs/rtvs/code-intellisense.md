---
title: "IntelliSense para código R Visual Studio | Microsoft Docs"
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
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 4e96184aa9a7711a7c046eb886049563dd308433
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="intellisense"></a>IntelliSense

O Visual Studio IntelliSense exibe informações sobre funções que você pode chamar, membros dos objetos, argumentos de função e [trechos de código](code-snippets.md) diretamente em sua exibição ao escrever código. Ele também exibe preenchimentos possíveis enquanto você digita e termina quando você pressiona as teclas Tab ou Enter (consulte [opções do editor](code-editing.md#editor-options) da guia **Avançado**). O IntelliSense está disponível no editor e na [janela interativa](interactive-repl.md).

![IntelliSense mostrando uma assinatura de função](media/intellisense-function-signature.png) 

Ao digitar uma função ou outra instrução, o IntelliSense fornece um menu de preenchimento automático filtrado (diferenciando maiúsculas de minúsculas ), de acordo com o que você já inseriu:

![Menu de preenchimento automático do IntelliSense](media/intellisense-auto-complete-menu.png)

Pressionar Tab (ou Enter ou Espaço, dependendo de como as opções são definidas), insere o item selecionado na lista suspensa. Você pode alterar a seleção com as teclas de direção. 

O IntelliSense também oferece sugestões para membros dos objetos R:
 
![Sugestões do IntelliSense para membros do objeto](media/intellisense-auto-complete-r-objects.png)
 
Pressionar ESC descarta o menu completamente. Você pode ativá-lo novamente com Ctrl + Espaço.

Digitar o `(` de abertura para uma chamada de função insere o `)` de fechamento e abre a Ajuda de assinatura conforme mostrado anteriormente:

![Ajuda de assinatura do IntelliSense para uma função](media/intellisense-function-signature.png)

Novamente, ESC descarta o popup; para assinaturas de função, você pode ativá-lo novamente com Ctrl + Shift + Espaço.

> [!Tip]
> Se a ajuda do parâmetro obscurecer o texto abaixo dela, pressione e segure a tecla Ctrl para tornar o texto da ajuda do parâmetro translucido.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense para funções e variáveis definidas pelo usuário

O IntelliSense aplica-se a funções definidas pelo usuário no mesmo arquivo, incluindo o preenchimento de parâmetro de nome:

![IntelliSense para funções definidas pelo usuário](media/intellisense-same-file-functions.png)

![Preenchimento de parâmetro do IntelliSense para funções definidas pelo usuário](media/intellisense-parameter-completion.png)

O IntelliSense também se aplica a variáveis no mesmo arquivo e na sessão atual:

![Preenchimento de variável do IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> Na janela interativa, o IntelliSense considera apenas nomes na sessão do R atual e ignora os arquivos em seu projeto.

## <a name="code-suggestions"></a>Sugestões de código

Quando uma lâmpada (chamada de smart tag) aparece na margem, o Visual Studio está sugerindo que um atalho está disponível para uma ação bastante usada. Por exemplo, passe o mouse sobre uma linha que contém uma instrução `library` no editor para ver uma lâmpada. Selecionar a lâmpada exibe as opções disponíveis:

![Smart tags para R no editor](media/intellisense-smart-tags.png)

