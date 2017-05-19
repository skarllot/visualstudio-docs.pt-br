---
title: Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 06f5b9d2223ccb9cbbbff8f2960d89c8efbf05b2
ms.openlocfilehash: 83a676c5f2f838b6920c5fafbe78dc9b49fbb4cb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---

# <a name="working-with-python-in-visual-studio"></a>Trabalhando com o Python no Visual Studio

O Python é uma linguagem de programação popular confiável, flexível, fácil de aprender, de uso gratuito em todos os sistemas operacionais e com suporte em uma sólida comunidade de desenvolvedores e várias bibliotecas gratuitas. O Python dá suporte a todas as formas de desenvolvimento, incluindo aplicativos Web, serviços Web, aplicativos de área de trabalho, scripts e computação científica e, da mesma forma, é usado por diversas universidades, vários cientistas e desenvolvedores casuais e profissionais. Saiba mais sobre a linguagem em [python.org](https://www.python.org) e em [Python para iniciantes](https://www.python.org/about/gettingstarted/).

O Visual Studio fornece suporte de [software livre](https://github.com/Microsoft/ptvs) para a linguagem Python por meio da carga de trabalho do Python (Visual Studio 2017) e a extensão gratuita Ferramentas Python para Visual Studio (Visual Studio 2015 e versões anteriores). 

Siga nossas [instruções de instalação](installation.md) para configurar a carga de trabalho do Python e, em seguida, use os links abaixo para saber mais sobre os recursos relacionados ao Python, bem como as funcionalidades do próprio Visual Studio.

| Recurso | Descrição | Documentação geral do Visual Studio | 
| --- | --- | --- |
| [Sistema de projeto do Visual Studio](python-projects.md) | Seleciona implicitamente uma estrutura de pastas do código do Python, ao mesmo tempo que permite o controle explícito para identificar o código de aplicativo, o código de teste, as páginas da Web, o JavaScript, os scripts de build, etc. | [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Modelos de projeto](python-projects.md#project-templates) | Cria rapidamente a estrutura do projeto para console, Web, Azure, ciência de dados e outros tipos de projetos | [Modelos do Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Suporte a vários interpretadores | Dá suporte a várias versões do CPython e do IronPython. | N/D |
| Suporte do IPython | Inclui suporte para o IPython/Jupyter no REPL para plotagens embutidas, .NET e WPF (Windows Presentation Foundation). | N/D |
| [Edição avançada, IntelliSense e compreensão de código](code-editing.md) | Inclui coloração de sintaxe, preenchimento automático em todo o código e todas as bibliotecas, [formatação de código](code-formatting.md), ajuda da assinatura, modo de exibição de classe, comandos Ir Para Definição e Localizar Todas as Referências, trechos de código, [refatoração](code-refactoring.md), [PyLint](code-pylint.md) e muito mais. | [Escrevendo código no editor de códigos e de texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Janela Interativa](interactive-repl.md) | Fornece uma experiência de REPL rápida para o Python com a capacidade de realçar com facilidade uma parte do código e enviá-lo para a Janela Interativa. | N/D |
| [Depuração completa](debugging.md) | A depuração pode ser feita com ou sem um projeto do Visual Studio, incluindo a capacidade de um executável existente, [depuração de modo misto do Python/C++](debugging-mixed-mode.md), [depuração remota](debugging-cross-platform-remote.md) para o Windows/Linux/Mac, [depuração remota para o Azure](debugging-azure-remote.md) e depuração na Janela Interativa. | [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Ferramentas de criação de perfil com relatórios abrangentes](profiling.md) | Explora como o tempo é gasto no aplicativo, incluindo a capacidade de comparar o desempenho entre diferentes execuções de criação de perfil. | [Ferramentas de Criação de Perfil](../profiling/profiling-tools.md) (nem todos os recursos de criação de perfil do Visual Studio estão disponíveis para o Python) |
| [Ferramentas de teste de unidade](unit-testing.md) | Descubra, execute e gerencie testes no Gerenciador de Testes do Visual Studio e depure testes de unidade com facilidade. | [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md) |

A carga de trabalho do Python também inclui o [SDK do Azure para Python](azure-sdk-for-python.md), que simplifica o consumo de serviços do Azure, com suporte para o Windows, Mac OS X e Linux.

Nossa série de [vídeos de introdução e aprofundamento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) no YouTube fornece uma visão geral dos principais recursos.

[![Vídeos das Ferramentas Python](media/video-general.png)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

## <a name="questions-and-answers"></a>Perguntas e Respostas

**P. O que pode ser usado para criar a interface do usuário com o Python?**

R. A oferta principal nessa área é o [Projeto Qt](https://www.qt.io/qt-for-application-development/), com associações de Python conhecidas como [PySide (a associação oficial)](http://wiki.qt.io/PySide) (consulte também [Downloads do PySide](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). No momento, o suporte do Python no Visual Studio não inclui quaisquer ferramentas específicas para desenvolvimento da interface do usuário.

**P. Um projeto do Python pode produzir um executável autônomo?**

R. Geralmente, o Python é uma linguagem interpretada, com o código executado sob demanda em um ambiente compatível com o Python, como o Visual Studio e servidores Web. No momento, o Visual Studio não fornece meios para criar um executável autônomo, o que, basicamente, é um programa com um interpretador de Python incorporado. No entanto, há vários meios dentro da comunidade do Python para fazer isso, conforme descrito em [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). O CPython também dá suporte a ser inserido em um aplicativo nativo, conforme descrito na postagem do blog [Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Usando o arquivo .zip que permite inserção do CPython).

## <a name="features-matrix"></a>Matriz de recursos

O suporte do Python pode ser instalado nas seguintes edições do Visual Studio, conforme descrito no [guia de instalação](installation.md):

- [Visualização do Visual Studio 2017](https://www.visualstudio.com/vs/preview)
- [Visual Studio 2015 (todas as edições)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- [Visual Studio 2013 Community Edition] (https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx)
- [Visual Studio 2013 Express para Web, Atualização 2 ou posterior](https://www.microsoft.com/en-us/download/details.aspx?id=44912)
- [Visual Studio 2013 Express para Área de Trabalho, Atualização 2 ou posterior](https://www.microsoft.com/en-US/download/details.aspx?id=44914)
- Visual Studio 2013 (edição Pro ou superior)
- Visual Studio 2012 (edição Pro ou superior)
- Visual Studio 2010 SP1 (edição Pro ou superior; o .NET 4.5 é necessário)

Recursos com suporte por versão e edição do Visual Studio:

| Suporte do Python | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Gerenciamento de vários interpretadores | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Detecção automática de interpretadores populares | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Adição de interpretadores personalizados | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ambientes Virtuais | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PIP/Fácil instalação | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Sistema de projeto | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Novo projeto com base em um código existente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mostrar todos os arquivos | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Controle do código-fonte | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Integração com o Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Edição | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Realce de sintaxe | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Preenchimento automático | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ajuda da assinatura | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Informações rápidas | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Modo de exibição de classe/pesquisador de objetos | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Barra de navegação | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ir para Definição | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Navegar para | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Localizar Todas as Referências | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Recuo automático | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formatação de código | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refatorar – renomear | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refatorar – extrair método | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refatorar – adicionar ou remover importação | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Janela Interativa | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Janela Interativa | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython com gráficos embutidos | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Desktop | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Aplicativo de console/do Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF do IronPython (com o designer XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Windows Forms do IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Projeto Web do Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projeto Web do Bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projeto Web do Flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projeto Web genérico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Implantação da Web para site | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Implantação da Web para função web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Implantação da Web para função de trabalho | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Execução no emulador do Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Depuração remota | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Anexação do Gerenciador de Servidores | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Modelos do Django | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Depuração | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Preenchimento automático | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Preenchimento automático para CSS e JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Depuração | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Depuração | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Depuração sem um projeto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Depuração – anexação à edição | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Depuração de modo misto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Depuração remota (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Janela interativa de depuração | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Criação de perfil | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Criação de perfil | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Teste | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Gerenciador de testes | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Executar teste | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Depurar teste | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. O suporte do Git para o VS 2012 está disponível nas Ferramentas do Visual Studio para a extensão do Git, disponível na [Galeria do Visual Studio](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

2. A implantação no Site do Azure exige o [SDK do Azure para .NET 2.1 – VS 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855).  Versões posteriores não dão suporte ao VS 2010.

3. O suporte à Função Web e à Função de Trabalho do Azure exige o [SDK do Azure para .NET 2.3 – VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) ou posterior.

4. O suporte à Função Web e à Função de Trabalho do Azure exige o [SDK do Azure para .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) ou posterior.

5. O editor de modelos do Django no Visual Studio 2013 apresenta alguns problemas conhecidos que foram resolvidos com a instalação da Atualização 2.

6. Exige o Windows 8 ou posterior. O Visual Studio 2013 Express para Web não tem a caixa de diálogo Anexar ao Processo, mas a depuração remota do Site do Azure ainda é possível com o comando Anexar Depurador (Python) no Gerenciador de Servidores. Isso exige o [SDK do Azure para .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) ou posterior.

7. Exige o Windows 8 ou posterior. O comando Anexar Depurador (Python) no Gerenciador de Servidores exige o [SDK do Azure para .NET 2.3 – VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) ou posterior.

8. Exige o Windows 8 ou posterior.

## <a name="additional-resources"></a>Recursos adicionais

- [Escrevendo jogos Kinect com o Python usando o PyKinect](https://github.com/Microsoft/PTVS/wiki/PyKinect) (wiki do GitHub)
- [Ponte do WFastCGI entre o IIS e o Python](https://pypi.python.org/pypi/wfastcgi) (python.org)

