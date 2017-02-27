---
title: "Introdução ao Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
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
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0

---
# <a name="getting-started-with-python-in-visual-studio"></a>Introdução ao Python no Visual Studio

O Python ([http://python.org/download/](http://python.org/download/)) é uma linguagem de programação popular que é confiável, flexível, fácil de aprender, de uso gratuito e com suporte de uma sólida comunidade de desenvolvedores e muitas bibliotecas gratuitas. O Python funciona com todos os principais sistemas operacionais e é útil para muitas finalidades, incluindo aplicativos Web, serviços Web, aplicativos de área de trabalho, scripts e computação científica. Sendo assim, ele é usado por muitas universidades, cientistas, desenvolvedores casuais e desenvolvedores profissionais.

Para saber mais sobre a linguagem, comece com [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python para iniciantes) (python.org).

## <a name="python-tools-for-visual-studio"></a>Ferramentas Python para o Visual Studio

As PTVS (Ferramentas Python para Visual Studio ) são uma extensão gratuita e de software livre para Visual Studio que oferecem experiência avançada de desenvolvimento Python, incluindo um sistema e modelos de projeto, IntelliSense e edição avançada, depuração completa e uma variedade de outras ferramentas.

A extensão oferece os seguintes recursos:

- Suporte para vários intérpretes: várias versões de CPython, IronPython e IPython
- Um sistema de projeto que seleciona implicitamente uma estrutura de pastas de código Python e também permite controle explícito, para que você possa identificar código de aplicativo, código de teste, páginas da Web, JavaScript, scripts de build e assim por diante.
- Modelos de projeto para console, Web, Azure, ciência de dados e outros tipos de projetos.
- Recursos de compreensão de código e edição avançada, incluindo coloração de sintaxe, preenchimento automático em todo o seu código e bibliotecas, ajuda com assinatura, modo de exibição de classe, Ir para Definição, Localizar Todas as Referências, refatoração e muito mais.
- Uma Janela Interativa (REPL)
- Depuração avançada sem um projeto do Visual Studio, a capacidade de depurar um executável existente, depuração de modo misto, depuração remota para Linux/Windows/Mac e depuração dentro da Janela Interativa.

- IPython com visualizações de dados.
- Suporte para IronPython e .NET/WPF.
- Ferramentas de criação de perfil.
- Ferramentas de teste.
- O [SDK do Azure para Python](#azure-sdk-for-python)

Os recursos a seguir o ajudarão a começar:

- [Instalar as Ferramentas Python para Visual Studio](https://www.visualstudio.com/vs/python/).
- [Guia de instalação](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [Introdução e vídeos de aprofundamento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- Instalação e demonstração de recursos (27 min)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [Documentação](https://github.com/Microsoft/PTVS/wiki)
- [Código-fonte](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>SDK do Azure para Python

O SDK do Azure para Python, que dá suporte a Windows, Mac e Linux, facilita o consumo e o gerenciamento de Serviços do Microsoft Azure. Consulte os recursos a seguir para obter detalhes:

- Para instalar o SDK, use o [Índice de pacote Python](https://pypi.python.org/pypi/azure) ou siga [Instalar o Python e o SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) na documentação do Azure.
- A [Central de desenvolvedores do SDK do Azure para Python](http://azure.microsoft.com/en-us/develop/python/) tem muita ajuda, da instalação à documentação, com tutoriais.  Veja alguns destaques:
- Guias de instruções:
  - [Armazenamento de blob](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [Fila de armazenamento](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [Tabela de página](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [Filas de barramento de serviço](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [Tópicos/assinaturas de barramento de serviço](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [Gerenciamento de serviços](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- O [Repositório do SDK no GitHub](https://github.com/Azure/azure-sdk-for-python) tem [testes de unidade](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests) que também são uma boa fonte de informações sobre APIs.


## <a name="scientific-computing"></a>Computação científica
Além de todas as bibliotecas de cientistas de dados do Python, as Ferramentas Python para Visual Studio dão suporte a IPython e IPython Notebooks, que podem ser hospedados no Azure.

É recomendável obter bibliotecas do IPython e de computação científica (matplotlib, scipy, numpy etc.) da [Universidade da Califórnia, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).

## <a name="see-also"></a>Consulte também
 [Introdução ao PTVS: instalando o Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [Introdução ao PTVS: iniciar a codificação (projetos)](../python/getting-started-with-ptvs-start-coding-projects.md)
 [Introdução ao PTVS: editando código](../python/getting-started-with-ptvs-editing-code.md)
 [Introdução ao PTVS: depurando](../python/getting-started-with-ptvs-debugging.md)
 [Introdução ao PTVS: Python interativo](../python/getting-started-with-ptvs-interactive-python.md)
 [Introdução ao PTVS: compilando um site no Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)


<!--HONumber=Feb17_HO4-->


