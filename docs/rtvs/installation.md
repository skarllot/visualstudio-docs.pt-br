---
title: Instalando as Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
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
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: bc0b1112fe6f3acf2605101a863d831f41bb5f6d
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>Como instalar as Ferramentas do R para Visual Studio

Neste tópico:

- [Versões do Visual Studio com suporte](#supported-versions-of-visual-studio)
- [Instalando as RTVS no Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Instalando as RTVS no Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Instalação offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Depois de instalar as Ferramentas do R, talvez você queira configurar o Visual Studio com um layout otimizado para cientista de dados, conforme descrito no tópico [Opções](options.md#data-scientist-layout).

## <a name="supported-versions-of-visual-studio"></a>Versões do Visual Studio com suporte

As RTVS (Ferramentas do R para Visual Studio) têm suporte nas edições Enterprise, Professional e Community do [Visual Studio 2015 Atualização 3 (ou posterior)](http://go.microsoft.com/fwlink/?LinkId=691129) e do [Visual Studio 2017](https://www.visualstudio.com/downloads/). 

As RTVS não serão instaladas se você tiver somente o Shell do Visual Studio incluído com outros produtos como o Visual Studio Test Professional e o SQL Server Management Studio. Isso ocorre porque o Shell do Visual Studio não tem os componentes necessários para as RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Instalando as RTVS no Visual Studio 2017

> [!Important]
> A instalação das RTVS no Visual Studio 2017 no Windows 7 está atualmente bloqueada, conforme descrito em [Problema #3561 do GitHub](https://github.com/Microsoft/RTVS/issues/3561). Esse problema será resolvido na atualização 15.3 do Visual Studio 2017.

1. Execute o instalador do Visual Studio.
2. Selecione a carga de trabalho **Ciência de dados e aplicativos analíticos**:

    ![Carga de trabalho de ciência de dados e aplicativos analíticos no VS2017](media/installation-data-science-workload.png)

3. Defina quaisquer opções adicionais no lado direito, sob o mesmo nome de carga de trabalho. Observe que, por padrão, essa carga de trabalho inclui suporte a F# e Python. Para R, você deve no mínimo selecionar **Suporte à linguagem R**, **Suporte de tempo de execução para desenvolvimento em R** e **Microsoft R Client**.

As RTVS são instaladas em: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` em que `<version>` é normalmente `2017` e `<edition>` é `Community`, `Professional` ou `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Instalando as RTVS no Visual Studio 2015

Com o Visual Studio 2015, você precisa instalar um interpretador de R e as Ferramentas do R separadamente.

### <a name="install-an-r-interpreter"></a>Instalar um interpretador de R

As RTVS requerem uma instalação de 64 bits do R versão 3.2.1 ou posterior em uma ou mais das seguintes fontes:

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

O Microsoft R Open e o CRAN R permitem várias versões lado a lado. O Microsoft R Client, no entanto, dá suporte a apenas uma versão e sempre usará a última que foi instalada.

### <a name="install-the-r-tools"></a>Instalar as Ferramentas R

Baixe as RTVS atuais de [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). As RTVS verificarão se há uma versão adequada do Visual Studio e também ajudarão você a instalar um interpretador de R, caso isso ainda não tenha sido feito.

As RTVS são instaladas em: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalação offline do Visual Studio e das RTVS

A instalação offline é adequada para computadores que não estão conectados à Internet:

1. Siga as instruções para criar um instalador offline para sua versão do Visual Studio, como indicado abaixo. 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Instale o Visual Studio do instalador offline.
1. [Baixe as RTVS](https://aka.ms/rtvs-current) e instale-as como de costume.

## <a name="see-also"></a>Consulte também

- [Introdução ao R](getting-started-with-r.md)
- [Projetos de exemplo das Ferramentas do R](getting-started-samples.md)
- [Obtendo ajuda](getting-started-help.md)
- [Configurações de opção](options.md)

