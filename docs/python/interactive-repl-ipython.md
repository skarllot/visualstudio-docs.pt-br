---
title: REPL do IPython no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 9553aa4944f652c7b8505b0d99d5c2b88167f872
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="using-ipython-in-the-interactive-window"></a>Usando o IPython na Janela Interativa

A janela interativa do Visual Studio no modo IPython é um ambiente avançado de desenvolvimento interativo, porém amigável, que contém recursos de Computação Paralela Interativa. Este tópico percorre o uso de IPython na janela interativa do Visual Studio, na qual todos os recursos normais de [janela interativa](interactive-repl.md) também estão disponíveis.

Para esse passo a passo, você deve ter o ambiente [Anaconda](https://www.continuum.io) instalado, que inclui o IPython e as bibliotecas necessárias.

> [!Note]
> O IronPython não dá suporte ao IPython, apesar do fato de ser possível selecioná-lo no formulário Opções Interativas. Para obter mais informações, consulte a [solicitação de recurso](https://github.com/Microsoft/PTVS/issues/84).

1. Abra o Visual Studio, mude para a janela Ambientes do Python (**Exibir > Outras Janelas > Ambientes do Python**) e selecione o ambiente do Python que apareceu quando você iniciou o IPython.

1. Examine a guia **Pacotes** ou (**pip**) e verifique se `IPython` e `matplotlib` estão listados. Caso contrário, instale-os nessa localização.

1. Selecione a guia **Visão Geral** e selecione **Usar o modo interativo do IPython.** (No Visual Studio 2015, selecione **Configurar opções interativas** para abrir a caixa de diálogo **Opções** e defina o **Modo Interativo** como IPython e selecione **OK**).    

1. Selecione **Abrir janela interativa** para exibir a janela interativa no modo IPython. Talvez você precise redefinir a janela se tiver acabado de mudar para o modo interativo, talvez você também precise pressionar Enter se apenas um prompt >>> aparecer.

    ![A janela interativa no modo IPython](media/ipython-repl-03.png)

1. Insira o seguinte código:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Depois de inserir a última linha, você deverá ver um gráfico embutido (que pode ser redimensionado arrastando o canto inferior direito), se desejado.

    ![Gráfico embutido na janela interativa](media/ipython-repl-04.png)

1. Em vez de digitar no REPL, é possível escrever o código no editor, selecioná-lo, clicar com o botão direito do mouse e selecionar o comando **Enviar para o Interativo** (ou pressionar Ctrl-Enter). Tente colar o código abaixo em um novo arquivo no editor, selecionando-o com Ctrl-A e enviando-o para a janela interativa. (Observe que o Visual Studio envia o código como uma unidade para evitar fornecer gráficos intermediários ou parciais. Observe também que se você não tiver um projeto do Python aberto com outro ambiente selecionado, o Visual Studio abrirá uma janela interativa para qualquer ambiente que esteja selecionado como seu padrão na janela **Ambientes do Python**.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![Enviando o código do editor para a janela interativa](media/ipython-repl-05.png)

1. Para ver os gráficos fora da janela interativa, execute o código em vez de usar o comando **Depurar > Iniciar sem Depuração**.
    
O IPython tem muitos outros recursos úteis, como escape para o shell do sistema, substituição de variáveis, captura de saída etc. Consulte a [documentação do IPython](http://ipython.org/documentation.html) para obter mais informações.

## <a name="related-topics"></a>Tópicos relacionados

- Para usar o Jupyter facilmente e sem instalação, experimente o [serviço hospedado dos Notebooks do Azure](https://notebooks.azure.com/) que permitem que você mantenha e compartilhe seus blocos de anotações com outras pessoas.

- Você também pode executar o Jupyter (anteriormente conhecido como IPython) em sua própria máquina virtual Windows ou Linux no Azure. Para obter detalhes, consulte [Criando uma VM do Azure, instalando o Jupyter e executando um Notebook do Jupyter no Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).

