---
title: "Recursos, cenários e ferramentas de teste do desenvolvedor | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit tests
ms.assetid: 9DE41406-8D39-427E-99D9-987E99103B73
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.sourcegitcommit: c559290c8e88c8b4e37feabc7014188fad15434d
ms.openlocfilehash: b36882588281fc95ff4814c148cd428d09196fa1
ms.contentlocale: pt-br
ms.lasthandoff: 06/08/2017

---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Recursos, cenários e ferramentas de teste do desenvolvedor

Mantenha a integridade do código com testes de unidade. O Visual Studio fornece uma ampla gama de técnicas e ferramentas avançadas para desenvolvedores para uso ao testar aplicativos:

**Cenários e funcionalidades:**

* [Evitar regressões e obter a cobertura de código com o IntelliTest](#intellitest)
* [Teste de interface do usuário com Selenium e IU Codificado](#ui-testing)
* [Teste de unidade efetivo com a cobertura de código do Visual Studio](#unit-testing)
* [Teste de unidade com qualquer estrutura usando o Gerenciador de Testes de alto desempenho](#test-explorer)
* [Introdução ao teste de unidade](getting-started-with-unit-testing.md)

<a name="intellitest"></a>
## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Evitar regressões e obter a cobertura de código com o IntelliTest

Em conjuntos de testes de unidade tradicionais, cada caso de teste representa um cenário de uso exemplar e as declarações incorporam a relação entre a entrada e a saída.  Verificar alguns desses cenários também pode ser suficiente, mas desenvolvedores experientes sabem que os bugs permanecem mesmo em códigos bem testados, quando testados, mas entradas não testadas provocam respostas erradas.

Melhore a cobertura e evite regressões com IntelliTest.
O IntelliTest reduz drasticamente o esforço de criação e manutenção de testes de unidade para códigos novos ou existentes. 

![IntelliTest em ação](media/devtest-intellitest.png)

* [Introduction to IntelliTest with Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx) (Introdução ao IntelliTest com o Visual Studio)
* [IntelliTest – One Test to rule them all](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx) (IntelliTest – um teste para controlar todos)
* [Vídeos do IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Introdução ao IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Manual de referência do IntelliTest](intellitest-manual/index.md)

<a name="ui-testing"></a>
## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Teste de interface do usuário com Selenium e IU Codificado

Teste sua interface do usuário com o que há de melhor com teste de interface do usuário aprovado pela comunidade.
Os testes de IU codificados fornecem uma maneira de criar testes totalmente automatizados para validar a funcionalidade e o comportamento da interface do usuário do seu aplicativo.
Eles podem automatizar o teste de interface do usuário em várias tecnologias, incluindo aplicativos da Windows Store com base em XAML, aplicativos de navegador e aplicativos SharePoint.

Quer você escolha o que há de melhor em testes de IU codificados ou teste de interface do usuário genérico com base no navegador com o Selenium, o Visual Studio fornece todas as ferramentas necessárias. 

![Testes de interface do usuário e interface do usuário codificada](media/devtest-codeduitest.png)

* [Usar automação de interface do usuário para testar código](use-ui-automation-to-test-your-code.md)
* [Introdução à criação, à edição e à manutenção do teste de IU codificado](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testar aplicativos da Windows Store com testes de UI codificados](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [Testar aplicativos da Windows Phone com testes de UI codificados](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [Testar aplicativos do SharePoint com testes de IU codificados](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Introdução aos testes de IU codificados com Visual Studio Enterprise (Laboratório)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

<a name="unit-testing"></a>
## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Teste de unidade efetivo com a cobertura de código do Visual Studio

Para determinar que proporção do código do projeto está sendo testada de fato por testes codificados, como os testes de unidade, você pode usar o recurso de cobertura de código do Visual Studio. Para se proteger efetivamente contra bugs, os testes devem utilizar ou abranger uma grande proporção de seu código.

A análise de cobertura de código pode ser aplicada ao código gerenciado (CLI) e não gerenciado (nativo).

A cobertura de código é uma opção quando você executa métodos de teste usando o Gerenciador de Testes. A tabela de resultados mostra a porcentagem do código que foi executada em cada assembly, classe e método. Além disso, o editor de código-fonte mostra que código foi testado.

![Testar com o Visual Studio Team Services e com o Team Foundation Server](media/devtest-codecoverage.png)

* [Usando cobertura de código para determinar quanto código está sendo testado](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Unit Testing, Code Coverage and Code Clone Analysis with Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx) (Teste de Unidade, Cobertura de Código e Análise de Clone de Código com o Visual Studio (Laboratório))
* [Personalizando a análise de cobertura de código](customizing-code-coverage-analysis.md)

<a name="test-explorer"></a>
## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>Teste de unidade com qualquer estrutura usando o Gerenciador de Testes de alto desempenho

O Gerenciador de Testes ajuda os desenvolvedores a criar, gerenciar e obter o máximo de benefício do teste de unidade.

![Gerenciador de Testes do Visual Studio](media/devtest-testexplorer.png)

* [Introdução ao Teste de Unidade](unit-test-your-code.md)
* [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md)
* [Escrevendo teste de unidade para C/C++](writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)
* [Instalar estruturas de teste de unidade de terceiros](install-third-party-unit-test-frameworks.md)

O Visual Studio também é extensível e abre a porta para adaptadores de teste de unidade de terceiros como o NUnit e o xUnit.net. Além disso, a capacidade de clone de código caminha lado a lado com a entrega de software de alta qualidade ajudando você a identificar blocos de código semanticamente semelhantes que podem ser candidatos para correções de bugs comuns ou refatoração.

![Integração de teste de terceiros](media/devtest-thirdparty.png)

## <a name="also-see"></a>Consulte também

* [Introdução ao teste de unidade](getting-started-with-unit-testing.md)
* [Speeding up Unit Test Execution in Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx) (Acelerando a execução do teste de unidade no Team Foundation Server)
* [Execução de teste de unidade paralela e sensível ao contexto](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Unit Testing, Code Coverage and Code Clone Analysis with Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx) (Teste de Unidade, Cobertura de Código e Análise de Clone de Código com o Visual Studio (Laboratório))

