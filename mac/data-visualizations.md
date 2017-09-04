---
title: "Depuração – Visualizações de dados"
description: "A depuração é uma parte comum e necessária da programação. O Visual Studio para Mac contém um pacote inteiro de recursos para facilitar a depuração. Este artigo examina as diferentes visualizações de dados que podem ser exibidas ao inspecionar objetos no depurador."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 5f1eda5ccf6f308c626d525bbe7069a84ce3154b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="data-visualizations"></a>Visualizações de dados

O Visual Studio para Mac inclui suporte da interface do usuário para o depurador, permitindo visualizações dos valores de uma variável, campo ou propriedade durante a depuração. Esses visualizadores de dados mostram uma versão estendida dos dados e permitem que os desenvolvedores inspecionem estruturas conhecidas, por exemplo, mostrando a cor de um struct de cores.

Os visualizadores no painel de depuração **Local** podem ser exibidos clicando no ícone de versão prévia que aparece à direita do valor quando o usuário focaliza a linha:

 ![Painel local](media/data-visualizations-image9.png)

A lista a seguir examina muitas das novas visualizações disponíveis durante a depuração no Visual Studio para Mac.

## <a name="point"></a>Ponto
Um Point/PointF ou CGPoint no iOS e no Mac será renderizado como uma tupla mostrando os valores X e Y no painel de depuração:

 ![Visualização de Ponto](media/data-visualizations-image10.png)

## <a name="size"></a>Tamanho
Um Size/SizeF ou CGSize no iOS e no Mac será renderizado como um retângulo. Ele é desenhada proporcionalmente até que uma dimensão aumente para além de 250px, quanto então o retângulo será escalado com a dimensão maior como 250px:

![Visualização de Tamanho](media/data-visualizations-image11.png)


## <a name="rectangle"></a>Retângulo
Um Rectangle/RectangleF ou CGRect no iOS e no Mac, exibirá as dimensões e a origem. Semelhante ao Tamanho, ela é desenhada proporcionalmente até que uma dimensão aumente para além de 250px:

 ![Visualização de Retângulo](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Coordenada
As coordenadas são plotadas em um mapa, com o local fixado no centro:

![Visualização de Coordenada](media/data-visualizations-image13.png)

## <a name="color"></a>Cor
Isso exibirá as propriedades UIColor, CGColor e Color, ilustrando a visualização de cores, os componentes RGBA, os valores de matiz-saturação-luminosidade e o valor hexadecimal da cor:

![Visualização de Cor](media/data-visualizations-image14.png)


## <a name="images"></a>Imagens

A mídia será renderizada proporcionalmente, até uma dimensão máxima de 250px e será escalada para caber quando a imagem exceder 250px:

 ![Visualização de Imagem](media/data-visualizations-image15.png)


## <a name="bezier-curves"></a>Curvas de Bézier

O visualizador exibirá um `NSBezierPath`:

![Visualização de curva de Bézier](media/data-visualizations-image16.png)


## <a name="string"></a>Cadeia de caracteres

Uma cadeia de caracteres inferior a 100 caracteres será exibida por completo, sem uma visualização. Cadeias de caracteres mais longas serão exibidas por completo na versão prévia. Cadeias de caracteres são editáveis e o visualizador acompanha um botão Editar para permitir que o valor de cadeia de caracteres seja editado na visualização ou no Editor de Valor de Cadeia de Caracteres, mostrado abaixo:

![Visualização de cadeia de caracteres](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Cadeias de caracteres pequenas:
![Visualização de cadeia de caracteres pequenas](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Cadeias de caracteres de tamanho médio:
![Visualização de cadeia de caracteres média](media/data-visualizations-image19.png)

### <a name="editor"></a>Editor:

 ![Visualização do Editor](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable enumera todos os valores e cada um deles pode ser exibido clicando no botão **Mostrar** valores. A opção de IEnumerable não exibe valores de objetos, como `Array`, `ArrayList`, `List<>` e `Dictionary<,>`, como eles têm seus próprios visualizadores do depurador.

![Visualização de IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Outros visualizadores

Alguns outros tipos que também têm seus próprios visualizadores embutidos estão listados abaixo:

 ![Outras visualizações](media/data-visualizations-image23.png)

*   **Primitives**
    *   Mostra o valor bruto do tipo primitivo.
*   **Enum**
    *   Exibe o valor do campo sem o qualificador do Tipo enumeração.
*   **Tuple**
    *   Exibido no formato (,)
*   **Null**
    *   Mostra o valor “null”.
*   **URL**
    *   Exite um hiperlink clicável.
*   **IntPtr**
    *   Exibe uma representação hexadecimal de IntPtr.

