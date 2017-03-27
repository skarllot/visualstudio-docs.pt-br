---
title: "Medindo o desempenho do código do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
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
ms.openlocfilehash: 2511f1076450848dfc75584edc97950fd4279c7b
ms.lasthandoff: 03/10/2017

---

# <a name="profiling-python-code"></a>Criação de perfil do código do Python

O Visual Studio dá suporte à criação de perfil de um aplicativo do Python ao usar interpretadores baseados em CPython.

A criação de perfil é iniciada por meio do comando de menu **Analisar > Iniciar Criação de Perfil do Python**, que abre uma caixa de diálogo de configuração:

![Caixa de diálogo de configuração de criação de perfil](media/profiling-start.png)

Quando você seleciona **OK**, o criador de perfil é executado e abre um relatório de desempenho por meio do qual é possível explorar como o tempo é gasto no aplicativo:

![Relatório de desempenho de criação de perfil](media/profiling-results.png)

Para obter uma visão geral, consulte o seguinte

Para obter uma demonstração passo a passo, assista ao vídeo [Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k) (Criação de perfil com as Ferramentas Python para Visual Studio) (8min52s).

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>Criação de perfil do IronPython

Como o IronPython não é um interpretador baseado em CPython, o recurso de criação de perfil acima não funcionará.

Em vez disso, use o criador de perfil do .NET do Visual Studio iniciando `ipy.exe` diretamente como o aplicativo de destino, usando os argumentos apropriados para iniciar o script de inicialização. Inclua `-X:Debug` na linha de comando para forçar todo o código do Python a ser depurável e passível à criação de perfil. Isso resulta em um relatório de desempenho, incluindo o tempo gasto no tempo de execução do IronPython e no código. O código é identificado usando nomes danificados.

Como alternativa, o IronPython tem alguns de seus próprios recursos de criação de perfis internos, mas atualmente não há nenhum visualizador adequado para eles. Consulte [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Um criador de perfil do IronPython) (blogs do MSDN) para ver o que está disponível.
