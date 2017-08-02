---
title: REPL do IPython no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>Usando o Python na Janela Interativa

A janela interativa do Visual Studio no modo IPython é um ambiente avançado de desenvolvimento interativo, porém amigável, que contém recursos de Computação Paralela Interativa. Neste tópico, explicaremos como usar o IPython na janela interativa do Visual Studio. Para isso, você deve ter o ambiente [Anaconda](https://www.continuum.io) instalado, que inclui o IPython e as bibliotecas necessárias.

> [!Note]
> O IronPython não dá suporte ao IPython, apesar do fato de ser possível selecioná-lo no formulário Opções Interativas. É possível votar a favor da [solicitação de recurso](https://github.com/Microsoft/PTVS/issues/84) ou implementá-lo, se desejar.

1. Verifique se o pacote do IPython está instalado corretamente acessando o diretório de instalação do Python e iniciando o IPython no modo Pylab:

  ```bash
  ipython --pylab
  ```

1. Insira o seguinte:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. Se tudo estiver configurado corretamente, você deverá ver algo parecido com isto:

    ![Saída de configuração do IPython ](~/python/media/ipython-repl-01.png)

1. Abra o Visual Studio, mude para a janela Ambientes do Python (**Exibir > Outras Janelas > Ambientes do Python**) e selecione seu ambiente do Python.
1. Examine a guia **PIP** e verifique se `IPython` e `matplotlib` estão listados. Caso contrário, instale-os nessa localização.
1. Selecione a guia **Visão Geral**, selecione **Configurar opções interativas**, defina **Modo Interativo** como IPython e selecione **OK**:

    ![Configurando o modo interativo como IPython](~/python/media/ipython-repl-02.png)

1. Selecione **Abrir janela interativa** para exibir a janela interativa no modo IPython com o PyLab. Talvez seja necessário redefinir a janela se você acabou de alterar o modo interativo:

    ![A janela interativa no modo IPython](~/python/media/ipython-repl-03.png)

1. Insira o seguinte código:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Depois de inserir a última linha, você deverá ver um gráfico embutido (que pode ser redimensionado arrastando o canto inferior direito), se desejado.

    ![Gráfico embutido na janela interativa](~/python/media/ipython-repl-04.png)

1. Em vez de digitar no REPL, é possível escrever o código no editor, selecioná-lo, clicar com o botão direito do mouse e selecionar o comando **Enviar para interativa** (Ctrl-E, E). Tente colar o código abaixo no editor, selecionando-o com Ctrl-A e enviando-o para a janela interativa. (Observe que quando o Visual Studio envia o código para a janela interativa, ele o envia como uma unidade, para evitar fornecer gráficos intermediários ou parciais.)

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

    ![Enviando o código do editor para a janela interativa](~/python/media/ipython-repl-05.png)

1. Para ver os gráficos fora da janela interativa, execute o código em vez de usar o comando **Depurar > Iniciar sem Depuração**.
    
1. O IPython tem vários recursos úteis, como escape para o shell do sistema, substituição de variáveis, captura de saída, etc. Consulte o guia de referência do IPython para obter mais informações:

    ![Escape para o shell do sistema](~/python/media/ipython-repl-06.png)

1. Também é possível usar o IPython no modo “bloco de anotações”, no qual é possível usar qualquer navegador em qualquer sistema operacional como a tela. O mecanismo de back-end do IPython pode ser local no computador ou remoto. O Azure tem suporte para a execução do [IPython em uma VM Windows ou Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook). Consulte também a [Visualização do Bloco de Anotações do Azure](https://notebooks.azure.com) para os Blocos de Anotações do Jupyter gratuitos como um Serviço no Azure:

    ![Modo de bloco de anotações do IPython](~/python/media/ipython-repl-07.png)

