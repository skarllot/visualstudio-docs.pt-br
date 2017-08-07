---
title: "Símbolos para a depuração de modo misto Python/C++ no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 1be4e28055f0501433f85325870654671c12f961
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Instalando símbolos de depuração para interpretadores do Python

Para fornecer uma experiência de depuração completa, o [depurador de modo misto do Python](debugging-mixed-mode.md) no Visual Studio precisa de símbolos de depuração para que o interpretador do Python sendo usado analise várias estruturas de dados internas. Para o python27.dll, por exemplo, o arquivo de símbolo correspondente é python27.pdb; para o python36.dll, o arquivo de símbolo é python36.pdb. Cada versão do interpretador também fornece arquivos de símbolo para diversos módulos.

Com o Visual Studio 2017, os interpretadores "Python 3" e "Anaconda 3" instalam automaticamente seus respectivos símbolos e o Visual Studio encontra esses símbolos de forma automática. No Visual Studio 2015 e versões anteriores ou ao usar outros interpretadores, é necessário baixar os símbolos separadamente e, em seguida, apontar o Visual Studio para eles por meio do diálogo **Ferramentas > Opções** na guia **Depuração > Símbolos**. Essas etapas são descritas nas seções a seguir.

É possível que o Visual Studio faça solicitações quando precisar de símbolos, normalmente ao iniciar uma sessão de depuração de modo misto. Nesse caso, ele exibe uma caixa de diálogo com duas opções:

- A **caixa de diálogo Abrir configurações de símbolo** abre a caixa de diálogo **Opções** para a guia **Depuração > Símbolos**.
- **Baixar símbolos para o interpretador** abrirá esta página de documentação, nesse caso, selecione, **Ferramentas > Opções** e navegue até a guia **Depuração > Símbolos** para continuar.

    ![Solicitação de símbolos de depuração de modo misto](media/mixed-mode-debugging-symbols-required.png)

## <a name="downloading-symbols"></a>Baixando símbolos

- Python 3.5 e versões posteriores: adquira símbolos de depuração por meio do instalador do Python. Selecione **Instalação personalizada**, selecione **Avançar** para ir para as **Opções Avançadas** e, em seguida, marque as caixas para **Baixar símbolos de depuração** e **Baixar binários de depuração**:

    ![Instalador do Python 3.x, incluindo símbolos de depuração](media/mixed-mode-debugging-symbols-installer35.png)

    Então, os arquivos de símbolo (`.pdb`) serão encontrados na pasta de instalação raiz (arquivos de símbolo para módulos individuais também estarão na pasta `DLLs`). Por isso, o Visual Studio os localiza automaticamente e nenhuma etapa adicional é necessária.

- Python 3.4.x e versões anteriores: os símbolos estão disponíveis como arquivos .zip para download em [distribuições oficiais](#official-distributions) ou [Enthought Canopy](#enthought-canopy). Após o download, extraia os arquivos para uma pasta local para continuar, como uma pasta `Symbols` dentro da pasta do Python.

    > [!Important]
    > Os símbolos são diferentes entre builds secundárias do Python e entre compilações de 32 e 64 bits, assim, é desejável que as versões sejam correspondentes. Para verificar o interpretador usado, expanda o **nó** *Ambientes do Python* do projeto no Gerenciador de Soluções e anote o nome do ambiente. Em seguida, mude para a **janela** *Ambientes do Python* e anote o local de instalação. Em seguida, abra uma janela de comando nesse local e inicie `python.exe`, que exibirá a versão exata e se ela é de 32 ou 64 bits.

- Para qualquer outra distribuição do Python de terceiros, como o ActiveState Python, será necessário entrar em contato com os autores dessa distribuição e solicitar que eles forneçam símbolos. No entanto, o WinPython incorpora o interpretador padrão do Python sem alterações; portanto, use símbolos da distribuição oficial para o número de versão correspondente.

## <a name="pointing-visual-studio-to-the-symbols"></a>Apontando o Visual Studio para os símbolos

Se os símbolos tiverem sido baixados separadamente, siga as etapas abaixo para que o Visual Studio os reconheça. Se os símbolos tiverem sido instalados por meio do Python 3.5 ou um instalador posterior, o Visual Studio os localizará automaticamente.

1. Selecione o menu **Ferramentas > Opções** e acesse **Depuração > Símbolos**.
    
1. Selecione o botão **Adicionar** na barra de ferramentas (descrita abaixo), digite a pasta em que os símbolos baixados foram expandidos (em que `python.pdb` está localizado, como `c:\python34\Symbols`, conforme mostrado abaixo) e selecione **OK**. 

    ![Opções de símbolos do depurador de modo misto](media/mixed-mode-debugging-symbols.png)

1. Durante uma sessão de depuração, o Visual Studio também pode solicitar o local de um arquivo de origem para o interpretador de Python. Se você baixou os arquivos de origem (de [python.org/downloads](https://www.python.org/downloads), por exemplo), certamente será possível apontar para eles também.

> [!Note]
> As funcionalidades de cache de símbolo mostradas no diálogo são usadas para criar um cache local de símbolos obtidos de uma fonte online. Essas funcionalidades não serão necessárias com os símbolos do interpretador de Python, uma vez que os símbolos já estão presentes localmente. Em qualquer caso, consulte [Especifique Símbolos e Arquivos de Origem no Depurador do Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) para obter mais detalhes.

## <a name="official-distributions"></a>Distribuições oficiais

| Versão do Python | Downloads | 
| --- | --- | 
| 3.5 e versões posteriores | Instale símbolos por meio do instalador do Python. | 
| 3.4.4 | [32 bits](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bits](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bits](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bits](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bits](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 bits](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bits](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 bits](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bits](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bits](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bits](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bits](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bits](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 bits](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 bits](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bits](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bits](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bits](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bits](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 bits](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bits](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bits](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bits](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bits](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bits](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bits](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 bits](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

O Enthought Canopy fornece símbolos para seus binários a partir da versão 1.2. Eles são instalados automaticamente juntamente com a distribuição, mas você ainda precisa adicionar manualmente a pasta que os contém ao caminho do símbolo, conforme descrito anteriormente. Para uma instalação típica por usuário do Canopy, os símbolos estão localizados em `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` para a versão de 64 bits e em `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` para a versão de 32 bits.

O Enthought Canopy 1.1 e anterior, bem como o EPD (Enthought Python Distribution), não fornecem símbolos de interpretador e, portanto, não são compatíveis com a depuração de modo misto.
