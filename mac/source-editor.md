---
title: "Editor de Código-fonte"
description: "Usar o editor de código-fonte no Visual Studio para Mac"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: aa7635cd2593b871128c0588110f0bfdad5a82ec
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="source-editor"></a>Editor de código-fonte

Um editor de código-fonte confiável é essencial para escrever código eficiente sucintamente. O Visual Studio para Mac fornece um editor de código-fonte sofisticados que centraliza suas interações com o IDE. O editor de código-fonte fornece os recursos que você pode esperar e precisa para realizar seu trabalho com facilidade: desde itens básicos como realce de sintaxe, trechos de código e dobramento de código, até os benefícios da sua integração com o compilador Roslyn, como preenchimento de código do IntelliSense totalmente funcional.

O editor de código-fonte no Visual Studio para Mac proporciona uma experiência perfeita com todas as outras funcionalidades fornecidas pelo IDE, como depuração, refatoração e integração de controle de versão.

Este tópico apresenta alguns dos principais recursos do editor de código-fonte e explora como você pode usar o Visual Studio para Mac para ser o mais produtivo possível.

## <a name="the-source-editor-experience"></a>A experiência do Editor de código-fonte

Exibir e mover com eficiência por todo o código faz parte integral do fluxo de trabalho de desenvolvimento. A maneira específica de como você decide exibir e manter o código é uma decisão pessoal, que varia entre os desenvolvedores e geralmente entre projetos.

O Visual Studio para Mac oferece muitos recursos poderosos para tornar o desenvolvimento de plataforma cruzada tão acessível e o mais útil possível. As seções a seguir descrevem alguns dos destaques.


### <a name="code-folding"></a>Dobramento de código

O dobramento de código facilita a tarefa de gerenciar arquivos de código-fonte grandes permitindo aos desenvolvedores mostrar ou ocultar seções completas do código, tal como o uso de diretivas, código clichê, comentários e instruções de #region. Isso é desativado por padrão no Visual Studio para Mac

Para habilitar o dobramento de código, navegue para **Visual Studio > Preferências... > Editor de texto > Geral > Dobramento de código**:

![Opções de dobramento de código](media/source-editor-image1.png)

Além de fornecer a opção para habilitar o dobramento de código, esse menu também inclui a opção de dobra #regions e comentários por padrão, exibindo uma dica nomeada, em vez de código.

Para mostrar ou ocultar seções, use o widget de divulgação de informações ao lado de número de linha:

 ![Mostrar ou ocultar seções no código](media/source-editor-image2.png)

Você também pode alternar entre mostrar e ocultar as dobras usando o item de menu **Exibir > Dobramento > Alternar Dobra / Alternar todas as dobras**:

 ![Item de Menu de Dobramento](media/source-editor-image19.png)

Este item de menu também pode ser usado para habilitar ou desabilitar o dobramento de código.

### <a name="white-space"></a>Espaço em branco

Pode ser necessário que você seja capaz de exibir caracteres invisíveis no código-fonte. É uma maneira visível de garantir que você está atendendo aos padrões de codificação e não desperdiçando espaço desnecessariamente. Isso também é muito útil ao escrever em F#, que depende de linhas recuadas com precisão para avaliar o código.

Defina as opções para mostrar o espaço em branco navegando para **Visual Studio > Preferências > Editor de texto > Marcadores e Réguas**, conforme ilustrado abaixo. Selecionar essa opção permite definir _quando_ os caracteres invisíveis serão exibidos: Nunca, Na seleção ou Sempre:

 ![Mostrar opções de caracteres invisíveis](media/source-editor-image3.png)

A opção para mostrar guias, espaços e terminações de linha também está disponível:

 ![Mostrar guias e espaços](media/source-editor-image4.png)

 Caracteres invisíveis são exibidos como pontos cinza, conforme ilustrado abaixo:

 ![espaço em branco exibido](media/source-editor-image22.png)


### <a name="ruler"></a>Régua

Mostrar a régua de coluna é útil para determinar os comprimentos de linhas, especialmente ao trabalhar em uma equipe com diretrizes de comprimento de linha. A régua de coluna pode ser ativada ou desativado navegando para **Visual Studio > Preferências... > Editor de texto > Marcadores e Réguas** e marcando (ou desmarcando) **Mostrar régua de coluna**, conforme ilustrado abaixo:

 ![](media/source-editor-image5.png)

 Ela é exibida como uma linha cinza clara vertical no editor de código-fonte.


### <a name="highlight-identifier-references"></a>Realçar as referências do identificador

Quando essa opção é ativada, um desenvolvedor pode colocar o cursor do mouse em qualquer símbolo no código-fonte e o editor de código-fonte fornecerá um guia visual para todas as outras referências nesse arquivo. Isso é ativado navegando para **Visual Studio > Preferências... > Editor de texto > Marcadores e Réguas** e selecionando _Realçar as referências do identificador_, conforme ilustrado abaixo:

![](media/source-editor-image6.png)

A cor de realce também útil para indicar que algo está sendo atribuído ou referenciado. Se algo for atribuído, ele será realçado em vermelho; se for referenciado, ele será realçado em azul:

![](media/source-editor-image7.png)




