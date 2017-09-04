---
title: "Criar stubs de método de teste de unidade com o comando Criar Testes de Unidade | Microsoft Docs"
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
ms.assetid: 5D625021-BA96-48A5-9453-3EF6F0943466
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
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 0bed76bf1dda027983bc960661937916b063a54e
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Criar stubs de método de teste de unidade com o comando Criar Testes de Unidade

O comando **Criar Testes de Unidade** do Visual Studio fornece a capacidade de criar stubs de método de teste de unidade. Esse recurso permite a configuração fácil de um projeto de teste, da classe de teste e do stub do método de teste dentro dele. 

## <a name="availability-and-extensions"></a>Disponibilidade e extensões

O comando de menu **Criar Testes de Unidade**:

* Está disponível nas edições Community, Professional e Enterprise do Visual Studio 2015 e posteriores.

* Dá suporte apenas ao código C# destinado ao .NET Framework.

* É [extensível](#extend-framework) e dá suporte a testes de emissão nos formatos MSTest, MSTest V2, NUnit e xUnit.

## <a name="get-started"></a>Introdução

Para começar, selecione um método, um tipo ou um namespace no editor de código no projeto que você deseja testar, abra o menu de atalho e escolha **Criar Testes de Unidade**. Isso abre a caixa de diálogo **Criar Testes de Unidade** em que as opções de criação para os novos testes de unidade podem ser selecionadas.

![Usando o comando Criar testes de unidade](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>Configurando as características do teste de unidade

Se você planeja executar esses testes como parte do processo de automação de teste, você poderá considerar criar o teste em outro projeto de teste (a segunda opção na caixa de diálogo acima) e configurar as características do teste de unidade para o teste de unidade. Isso permitirá que você inclua ou exclua mais facilmente esses testes específicos como parte de uma integração contínua ou pipeline de implantação contínua. As características são definidas pela adição de metadados ao teste de unidade diretamente, conforme mostrado abaixo. 

![Configurando as características do teste de unidade](media/createunittest.png)

<a name="extend-framework"></a>
## <a name="using-third-party-unit-test-frameworks"></a>Usando estruturas de teste de unidade de terceiros

Com o Visual Studio, você pode facilmente criar testes de unidade usando qualquer estrutura de teste. Para instalar e adicionar outras estruturas de teste, escolha **Ferramentas | Extensões e Atualizações**.
Expanda **Online**, **Galeria do Visual Studio**, **Ferramentas** e escolha **Teste**. 

![Usando estruturas de teste de terceiros](media/createunittestfx.png)

As extensões da estrutura de teste também estão disponíveis no Visual Studio Marketplace:

* [Extensão do NUnit para geradores de teste](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Extensão do xUnit.net para geradores de teste](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Quando devo usar esse recurso?

Use este recurso sempre que precisar criar testes de unidade, mas especialmente quando estiver testando o código existente que tem muito pouca ou nenhuma cobertura do teste e nenhuma documentação. Em outras palavras, onde há especificação de código limitada ou inexistente. Ele implementa efetivamente uma abordagem semelhante aos [Testes de Unidade Inteligentes](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) que caracterizam o comportamento observado do código.

No entanto, esse recurso é igualmente aplicável para a situação em que o desenvolvedor começa escrevendo um código e o usa para inicializar a disciplina de teste de unidade. Dentro do fluxo de codificação, o desenvolvedor talvez queira criar rapidamente um stub de método de teste de unidade (com uma classe de teste adequada e um projeto de teste adequado) para uma determinada parte do código. 

## <a name="more-information"></a>Mais informações

Consulte a postagem do blog [Creating unit test method stubs with "Create Unit Tests"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/) (Criar stubs de método de teste de unidade com “Criar Testes de Unidade”).

É possível encontrar mais postagens de blog de teste de unidade [aqui](https://blogs.msdn.microsoft.com/visualstudioalm/tag/unit-testing/).

