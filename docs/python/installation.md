---
title: "Instalação do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 613af31a2e44cc447980b68de4b0b5642dde1262
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="installing-python-support-in-visual-studio-on-windows"></a>Instalando o suporte do Python no Visual Studio no Windows

Para instalar o suporte do Python para Visual Studio, siga as instruções da seção que corresponde à sua versão do Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 e anterior](#visual-studio-2013-and-earlier)

Para o Visual Studio 2015 e anterior, também é necessário instalar separadamente um interpretador do Python de sua escolha. Para obter detalhes, consulte [Ambientes do Python](python-environments.md).

Para testar rapidamente o suporte do Python depois de seguir as etapas de instalação, abra a janela Interativa do Python pressionando Alt-I e inserindo `2+2`. Se você não vir a saída de `4`, verifique as etapas novamente.

> [!Tip]
> A carga de trabalho do Python inclui a extensão útil Cookiecutter, que fornece uma interface gráfica do usuário para descobrir modelos e opções de modelo de entrada e criar projetos e arquivos. Para obter detalhes, consulte [Usando o Cookiecutter](cookiecutter.md).

> [!Note]
> O suporte ao Python não está disponível atualmente no Visual Studio para Mac, mas está disponível no Mac e no Linux por meio do Visual Studio Code. Consulte [Perguntas e respostas](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Instale o Visual Studio 2017 em [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/).

1. No instalador do Visual Studio, selecione a carga de trabalho **Web e Nuvem > Desenvolvimento do Python**.

    ![Carga de trabalho de desenvolvimento do Python no instalador do Visual Studio](media/installation-python-workload.png)

    > [!Note]
    > O Python também está incluído na carga de trabalho de **Ciência de dados e aplicativos analíticos**.

1. No lado direito do instalador, selecione os interpretadores do Python e outras ferramentas relacionadas que você deseja incluir. Por exemplo, se você pretende desenvolver extensões do C++ para o Python, inclua a opção **Ferramentas de desenvolvimento nativo do Python**.

    ![Opções de desenvolvimento do Python no instalador do Visual Studio](media/installation-python-options.png)

1. Se você já tiver interpretadores instalados em seu computador, consulte [Criando um ambiente para um interpretador existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Execute o instalador do Visual Studio por meio do **Painel de Controle > Programas e Recursos**, selecionando **Microsoft Visual Studio 2015** e, em seguida, **Alterar**.

1. No instalador, selecione **Modificar**.

1. Selecione **Linguagens de Programação > Ferramentas Python para Visual Studio** e, em seguida, **Avançar**:

    ![Opção PTVS no instalador do Visual Studio 2015](media/installation-vs2015.png)    

1. Depois que a instalação do Visual Studio for concluída, [instale um interpretador do Python de sua escolha](python-environments.md#selecting-and-installing-python-interpreters). Se você já tiver um interpretador instalado, consulte [Criando um ambiente para um interpretador existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 e anterior

1. Instale a versão apropriada das Ferramentas Python para Visual Studio para sua versão do Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 para Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). A caixa de diálogo **Arquivo > Novo Projeto** no Visual Studio 2013 fornece um atalho para esse processo.
    - Visual Studio 2012: [PTVS 2.1 para Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 para Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Instale um interpretador do Python de sua escolha](python-environments.md#selecting-and-installing-python-interpreters). Se você já tiver um interpretador instalado, consulte [Criando um ambiente para um interpretador existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Locais de instalação

Por padrão, o suporte do Python é instalado para todos os usuários em um computador.

Para o Visual Studio 2017, a carga de trabalho do Python é instalada em `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, em que &lt;VS_edition&gt; é Community, Professional ou Enterprise.

Para o Visual Studio 2015 e anterior, os caminhos de instalação são os seguintes:

- 32 bits:
  - Caminho: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Local do Registro do caminho: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bits:
  - Caminho: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Local do Registro do caminho: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

em que:

- &lt;VS_ver&gt; é:    
    - 14.0 para Visual Studio 2015
    - 12.0 para Visual Studio 2013
    - 11.0 para Visual Studio 2012
    - 10.0 para Visual Studio 2010
- &lt;PTVS_ver&gt; é um número de versão, como 2.2, 2.1, 2.0, 1.5, 1.1 ou 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalações específicas ao usuário (1.5 e anterior)

A instalação das Ferramentas Python para o Visual Studio 1.5 e anteriores é permitida somente para o usuário atual. O caminho de instalação é `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`, em que &lt;VS_ver&gt; e &lt;PTVS_ver&gt; são iguais ao descrito acima.

