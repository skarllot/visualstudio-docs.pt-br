---
title: "Introdução ao teste de unidade – criar planos de teste | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit testing, create unit test plans
ms.assetid: 2171CD69-FBB1-4994-9DCC-3BFFDFD26662
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
ms.openlocfilehash: 576b8b744d24a456c16724cb5ae7e65a73a769db
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="get-started-with-unit-testing"></a>Introdução ao teste de unidade

Use o Visual Studio para definir e executar os testes de unidade para manter a integridade de código, certificar-se da cobertura de código e localizar erros e falhas antes de seus clientes.

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>Criar testes de unidade

Crie testes de unidade e execute-os frequentemente para ter certeza de que seu código está funcionando corretamente.

1. Crie um projeto de teste de unidade.
        
   ![Adicionar um projeto de teste de unidade à sua solução](media/createunittest1.png)
    
1. Nomeie o projeto.
        
   ![Modelo de projeto de teste de unidade](media/createunittest2.png)
  
   O projeto é adicionado à solução.
    
   ![Projeto de teste de unidade no Gerenciador de Soluções](media/createunittest5.png)
    
1. No projeto de teste de unidade, adicione uma referência ao projeto que deseja testar.
        
   ![Adicionar uma referência ao seu projeto de teste de unidade](media/createunittest6.png)
    
1. Selecione o projeto que contém o código que você testará.
        
   ![Selecionar a referência a ser adicionada](media/createunittest7.png)
    
1. Codifique seu teste de unidade.

   ![Adicionar código ao teste de unidade](media/createunittest8.png) 

Você também pode criar stubs de método de teste de unidade com o [comando **Criar Testes de Unidade**](create-unit-tests-menu.md).
Ou você pode usar uma [estrutura de teste de unidade diferente](#frameworks) para criar testes para linguagens de código diferente.

![Usando o comando Criar testes de unidade](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Executar testes de unidade

1. Abra o Gerenciador de Testes.
        
   ![No menu Teste, abra o Gerenciador de testes](media/rununittest1.png) 

1. Execute os testes de unidade.
        
   ![Executar testes de unidade no Gerenciador de Testes](media/rununittest2.png) 

   Você pode ver os testes de unidade que foram aprovados ou falharam no Gerenciador de Testes.
      
   ![Examine os resultados de teste de unidade no Gerenciador de Testes](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>Exibir resultados de teste de unidade em tempo real

Se você estiver usando a estrutura de teste do MSTest, do xUnit ou do NUnit no Visual Studio de 2017 ou acima, poderá ver os resultados em tempo real de seus testes de unidade na interface do usuário do Visual Studio.

1. Ative o teste de unidade em tempo real no menu **Teste**.

   ![Ativar o teste de unidade em tempo real](media/live-test-results-start.png) 

1. Exiba os resultados dos testes dentro da janela do editor de código conforme você escreve e edita o código.

   ![Apontar para e clicar nos indicadores de resultado do teste](media/live-test-results-ui.png) 

1. Aponte para e clique nos indicadores de resultados do teste para obter mais informações.

   ![Exibir os resultados dos testes](media/live-test-results-details.png) 

Para obter mais detalhes, consulte [Live Unit Testing in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/) (Live Unit Testing no Visual Studio).

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>Gerar testes de unidade com IntelliTest

Quando executa o IntelliTest, você pode ver facilmente quais testes estão falhando e adicionar o código que for necessário para corrigi-los. É possível selecionar quais dos testes gerados serão salvos em um projeto de teste para oferecer um pacote de regressão. Conforme você alterar seu código, execute novamente o IntelliTest para manter os testes gerados em sincronia com as alterações do código. Para saber como, consulte [Gerar testes de unidade para seu código com o IntelliTest](https://docs.microsoft.com/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest).

![Gerando testes de unidade com IntelliTest](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>Executar testes de unidade com o Gerenciador de Testes

Use o Gerenciador de Testes para executar testes de unidade do Visual Studio ou projetos de teste de unidade de terceiros, agrupar testes em categorias, filtre a lista de testes, criar, salvar e executar as listas de reprodução de testes. Você também pode depurar testes e analisar um teste de desempenho e cobertura de código. Para saber como, consulte [Executar testes de unidade com o Gerenciador de Testes](https://docs.microsoft.com/visualstudio/test/run-unit-tests-with-test-explorer).

![Executando testes de unidade com o Gerenciador de Testes](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usar a cobertura de código para determinar quanto do código está sendo testado

Para determinar que proporção do código do projeto está sendo testada de fato por testes codificados, como os testes de unidade, você pode usar o recurso de cobertura de código do Visual Studio. Para se proteger efetivamente contra bugs, os testes devem utilizar ou "cobrir" uma grande proporção de seu código. Para saber como, consulte [Usar a cobertura de código para determinar quanto do código está sendo testado](https://docs.microsoft.com/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested).

![Usando a cobertura de código para determinar quanto código está sendo testado](media/codecoverage.png)

## <a name="q--a"></a>Perguntas e respostas

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks"></a>
####Posso executar testes de unidade no Visual Studio se eu usar uma estrutura diferente de teste de unidade?

R: sim, use o plug-in para essa estrutura para que o executor de teste do Visual Studio possa funcionar com ela. Aqui estão alguns dos [plug-ins de estrutura de teste de unidade para o Visual Studio](http://go.microsoft.com/fwlink/?LinkID=246630).

1. Use o gerenciador de extensões do Visual Studio para baixar seu plug-in.
        
   ![Selecione plug-ins de teste de unidade de terceiros com o gerenciador de extensões](media/install3rdpartyunittestframeworks1.png) 

1. Baixe o plug-in da Galeria do Visual Studio, em Ferramentas/Teste ou pesquise por ele se souber o nome.
        
   ![Baixar o plug-in](media/install3rdpartyunittestframeworks2.png) 

1. Crie um projeto de biblioteca de classes.
        
   ![Criar um projeto de biblioteca de classes](media/create3rdpartyunittest1.png) 

   Adicione o projeto à sua solução.
    
   ![Atribua um nome ao projeto de biblioteca de classes e adicione-o](media/create3rdpartyunittest3.png) 

1. No projeto de biblioteca de classes, execute NuGet para instalar o plug-in.

   ![Gerenciar pacotes NuGet para instalar o plug-in](media/create3rdpartyunittest3a.png) 

   O [NuGet](https://www.nuget.org/) é uma extensão do Visual Studio que pode ser usada para adicionar e atualizar bibliotecas e ferramentas dos seus projetos.

1. Instale seu plug-in. Se souber o nome, você poderá pesquisar por ele na Internet.

   ![Instalar a estrutura de terceiros](media/create3rdpartyunittest4.png) 

   A estrutura é referenciada no seu projeto.
        
   ![A referência para a estrutura de teste de unidade de terceiros é adicionada à solução](media/create3rdpartyunittest6.png) 

1. No projeto de biblioteca de classes, adicione uma referência ao projeto que deseja testar.
        
   ![Adicionar uma referência ao projeto](media/createunittest6.png) 

1. Selecione o projeto que contém o código que você testará.
        
   ![Selecione o projeto de código para testar](media/createunittest7.png) 

1. Codifique seu teste de unidade.

   ![Adicionar código ao teste de unidade](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>Consulte também

* [Criar comando de Testes de Unidade](create-unit-tests-menu.md)
* [Gerar testes com IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Executar testes com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md)
* [Determinar a cobertura de código](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Melhorar a qualidade do código](improve-code-quality.md)

