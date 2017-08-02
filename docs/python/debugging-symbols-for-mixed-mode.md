---
title: "Símbolos para a depuração de modo misto Python/C++ no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/4/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
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
ms.sourcegitcommit: adf122a478b29674dc2924dcf7d42972a5a3f52e
ms.openlocfilehash: b8bf362f506255c09468934f01a7beeef3a632dd
ms.lasthandoff: 04/10/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Instalando símbolos de depuração para interpretadores do Python

Para fornecer uma experiência de depuração completa, o [depurador de modo misto do Python](debugging-mixed-mode.md) no Visual Studio precisa analisar diversas estruturas de dados internas no interpretador do Python que está sendo usado. Isso exige símbolos de depuração para o próprio interpretador. Para o python27.dll, por exemplo, o arquivo de símbolo correspondente é python27.pdb; para o python36.dll, o arquivo de símbolo é python36.pdb. Cada versão do interpretador também fornece arquivos de símbolo para diversos módulos.

Com o Visual Studio 2017, os interpretadores "Python 3" e "Anaconda 3" instalam automaticamente seus respectivos símbolos e o Visual Studio os encontrará de forma automática. No Visual Studio 2015 e versões anteriores ou ao usar outros interpretadores, será necessário baixar os símbolos separadamente e, em seguida, apontar o Visual Studio para eles por meio do diálogo **Ferramentas > Opções** na guia **Depuração > Símbolos**. Essas etapas são descritas nas seções a seguir.

É possível que o Visual Studio faça solicitações quando precisar de símbolos, normalmente ao iniciar uma sessão de depuração de modo misto. Nesse caso, ele exibirá um diálogo com duas opções:

- A **caixa de diálogo Abrir configurações de símbolo** abre a caixa de diálogo **Opções** para a guia **Depuração > Símbolos**.
- **Baixar símbolos para o interpretador** abrirá esta página de documentação, nesse caso, selecione, **Ferramentas > Opções** e navegue até a guia **Depuração > Símbolos** para continuar.

    ![Solicitação de símbolos de depuração de modo misto](~/docs/python/media/mixed-mode-debugging-symbols-required.png)

## <a name="downloading-symbols"></a>Baixando símbolos

- Python 3.5 e versões posteriores: adquira símbolos de depuração por meio do instalador do Python. Selecione **Instalação personalizada**, selecione **Avançar** para ir para as **Opções Avançadas** e, em seguida, marque as caixas para **Baixar símbolos de depuração** e **Baixar binários de depuração**:

    ![Instalador do Python 3.x, incluindo símbolos de depuração](~/docs/python/media/mixed-mode-debugging-symbols-installer35.png)

    Então, os arquivos de símbolo (`.pdb`) serão encontrados na pasta de instalação raiz (arquivos de símbolo para módulos individuais também estarão na pasta `DLLs`). Por isso, o Visual Studio os localizará automaticamente e nenhuma etapa adicional será necessária.

- Python 3.4.x e versões anteriores: os símbolos estão disponíveis como arquivos .zip para download em [distribuições oficiais](#official-distributions) ou [Enthought Canopy](#enthought-canopy), conforme indicado abaixo. Após o download, extraia os arquivos para uma pasta local para continuar, como uma pasta `Symbols` dentro da pasta do Python.

    > [!Important]
    > Os símbolos são diferentes entre compilações secundárias do Python e entre compilações de 32 e 64 bits, assim, é desejável que as versões sejam correspondentes. Para verificar o interpretador usado, expanda o **nó** *Ambientes do Python* do projeto no Gerenciador de Soluções e anote o nome do ambiente. Em seguida, mude para a **janela** *Ambientes do Python* e anote o local de instalação. Em seguida, abra uma janela Comando nesse local e inicie `python.exe`, que exibirá a versão exata e se ela é de 32 ou 64 bits.

- Para qualquer outra distribuição do Python de terceiros, como o ActiveState Python, será necessário entrar em contato com os autores dessa distribuição e solicitar que eles forneçam símbolos. No entanto, o WinPython incorpora o interpretador padrão do Python sem alterações; portanto, use símbolos da distribuição oficial para o número de versão correspondente.

## <a name="pointing-visual-studio-to-the-symbols"></a>Apontando o Visual Studio para os símbolos

Se os símbolos tiverem sido baixados separadamente, siga as etapas abaixo para que o Visual Studio os reconheça. Se os símbolos tiverem sido instalados por meio do Python 3.5 ou um instalador de versão posterior, o Visual Studio os localizará automaticamente.

1. Selecione o menu **Ferramentas > Opções** e acesse **Depuração > Símbolos**.
    
1. Selecione o botão Adicionar na barra de ferramentas (descrita abaixo), digite a pasta em que os símbolos baixados foram expandidos (em que `python.pdb` está localizado, como `c:\python34\Symbols`, conforme mostrado abaixo) e selecione **OK**. 

    ![Opções de símbolos do depurador de modo misto](~/docs/python/media/mixed-mode-debugging-symbols.png)

1. Durante uma sessão de depuração, o Visual Studio também pode solicitar o local de um arquivo de origem para o interpretador de Python. Se você baixou esses (de [python.org/downloads](https://www.python.org/downloads), por exemplo), certamente será possível apontar para eles também.

> [!Note]
> As funcionalidades de cache de símbolo mostradas no diálogo são usadas para criar um cache local de símbolos obtidos de uma fonte online. Essas funcionalidades não serão necessárias com os símbolos do interpretador de Python, pois você já as terá baixado localmente. Em qualquer caso, consulte [Especifique Símbolos e Arquivos de Origem no Depurador do Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) para obter mais detalhes.

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

O Enthought Canopy fornece símbolos para seus binários a partir da versão 1.2. Eles são instalados automaticamente juntamente com a distribuição, mas você ainda precisará adicionar manualmente a pasta que os contém ao caminho do símbolo, conforme descrito anteriormente. Para uma instalação típica por usuário do Canopy, os símbolos estão localizados em `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` para a versão de 64 bits e em `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` para a versão de 32 bits.

O Enthought Canopy 1.1 e anterior, bem como o EPD (Enthought Python Distribution), não fornecem símbolos de interpretador e, portanto, não são compatíveis com a depuração de modo misto.
