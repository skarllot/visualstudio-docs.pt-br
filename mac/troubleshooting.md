---
title: "Solução de problemas"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a820423704b6f656b55b7e33f15d1c7880d2e27d
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="troubleshooting"></a>Solução de problemas

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Exibindo logs no Visual Studio para Mac
 
Os logs podem ser encontrados navegando para o item de menu **Ajuda > abrir Diretório de Log**, conforme ilustrado abaixo:

![Item de menu Abrir diretório de logs](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Exibição de exceções

Quando uma exceção é detectada, uma bolha de exceção é exibida. Para exibir mais detalhes, selecione o botão **Exibir detalhes**:

![Exibir mais detalhes sobre uma exceção](media/troubleshooting-image2.png)

Isso exibirá a caixa de diálogo **Mostrar detalhes**, fornecendo mais informações sobre a exceção:

![](media/troubleshooting-image3.png)

Seções importantes da caixa de diálogo, numeradas acima, são descritas em detalhes a seguir:

1. O tipo de exceção, que mostra o nome completo do tipo de exceção que está sendo observado.
2. A mensagem de exceção, que mostra o valor da propriedade Message do objeto de exceção.
3. O tipo de exceção interna, que mostra o nome completo do tipo de exceção para a exceção selecionada no momento no modo de exibição de árvore de Exceção interna.
4. A mensagem da Exceção interna, que mostra o valor da propriedade Message da exceção selecionada no modo de exibição de árvore Exceção interna.
5. Exibição de rastreamento de pilha. Pode ser recolhida por meio de uma seta de divulgação de informações e contém entradas de registros de ativação.
6. Exemplo de entradas de código que não são do usuário.
7. Exemplo de entradas de código do usuário.
8. Exibição Propriedades, que mostra todas as propriedades e campos da exceção. Pode ser recolhida por meio de uma seta de divulgação.
9. Modo de exibição de árvore de Exceção interna. Selecione as exceções internas nesta exibição usando as teclas para cima/para baixo do tecla, com o mouse ou com o trackpad.
10. Por padrão, isso é definido para o mesmo que a opção **Depurar somente o código do projeto** nas configurações do depurador. Marcar essa caixa permitirá que todo o código que não é do usuário seja recolhido em uma linha no rastreamento de pilha.
11. Um botão Copiar para copiar a saída de `exception.ToString()` para a área de transferência.

Observe que algumas dessas seções só ficarão visíveis quando a exceção tiver uma exceção interna.
