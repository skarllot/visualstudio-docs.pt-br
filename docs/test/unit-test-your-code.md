---
title: "Efetuar teste de unidade em seu código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 62
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 1a47ab6e11e4c67713961078f125bb7abca23bb9
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="unit-test-your-code"></a>Teste de unidade de código
Os testes de unidade fornecem aos desenvolvedores e testadores uma maneira rápida de procurar por erros lógicos nos métodos de classes em projetos do [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], do [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] e do [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].  
  
 As ferramentas de testes de unidade incluem:  
  
1.  **Gerenciador de testes.** O Gerenciador de Testes permite realizar testes de unidade e exibir seus resultados. O Gerenciador de Testes pode usar qualquer framework de teste de unidade, incluindo framework de terceiros, que tenha um adaptador para o Explorer.  
  
2.  **Framework de teste de unidade da Microsoft para código gerenciado.** O framework de testes de unidade da Microsoft para código gerenciado é instalado com o Visual Studio e fornece um framework para testar o código .NET.  
  
3.  **Framework de teste de unidade da Microsoft para C++.** O framework de testes de unidade da Microsoft para C++ é instalado com o Visual Studio e fornece um framework para testar o código nativo.  
  
4.  **Ferramentas de cobertura de código.** É possível determinar a quantidade de código do produto que seus testes de unidade utilizam com um comando no Gerenciador de Testes.  
  
5.  **Framework de isolamento do Microsoft Fakes.** O framework de isolamento do Microsoft Fakes pode criar classes e métodos substitutos para o código de produção e de sistema que criam dependências do código em teste. Ao implementar os delegados falsos para uma função, você controla o comportamento e a saída do objeto de dependência.  
  
 Você também pode usar o [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) para explorar seu código .NET para gerar dados de teste e um conjunto de testes de unidade. Para cada instrução no código, é gerada uma entrada de teste para executar essa instrução. Uma análise de caso é realizada para cada branch condicional do código.  
  
## <a name="key-tasks"></a>Tarefas-chave  
 Use os tópicos a seguir como auxílio para entender e criar testes de unidades:  
  
|Tarefas|Tópicos associados|  
|-----------|-----------------------|  
|**Guias de início rápido e passo a passo:** use os tópicos a seguir para aprender sobre teste de unidade no Visual Studio a partir de exemplos de código.|-   [Passo a passo: criação e execução de testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Início rápido: desenvolvimento orientado por testes com o gerenciador de testes](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Adição de testes de unidade a aplicativos do C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Código nativo de teste de unidade com o gerenciador de testes](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Teste de unidade com o gerenciador de testes:** saiba como o gerenciador de testes pode ajudar a criar testes de unidade mais produtivos e eficientes.|-   [Noções básicas de teste de unidade](../test/unit-test-basics.md)<br />-   [Criação de um projeto de teste de unidade](../test/create-a-unit-test-project.md)<br />-   [Execução de testes de unidade com o gerenciador de testes](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalação de frameworks de teste de unidade de terceiros](../test/install-third-party-unit-test-frameworks.md)<br />-   [Atualização de testes de unidade a partir do Visual Studio 2010](http://msdn.microsoft.com/en-us/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Código gerenciado de teste de unidade:**|-   [Como escrever testes de unidade para .NET Framework com o framework de teste de unidade da Microsoft para código gerenciado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Teste de unidade de código C++**|-   [Como escrever testes de unidade para C/C++ com o framework de testes de unidade da Microsoft para C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolamento de testes de unidade**|-   [Isolamento de código em teste com Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Uso da cobertura de código para identificar quais proporções do código do projeto estão sendo testadas usando os testes de unidade:** saiba mais sobre o recurso de cobertura de código das ferramentas de teste do [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)].|-   [Uso da cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Execução de análise de estresse e desempenho usando testes de carga para seus testes de unidade:** você pode criar um teste de carga e adicionar seus testes de unidade a ele para ajudar a isolar os problemas de estresse e desempenho em seu aplicativo. **Nota:** a criação e utilização dos testes de carga requerem o Visual Studio Enterprise.|-   [Criação e edição de testes de carga](http://msdn.microsoft.com/en-us/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Como: adicionar testes de desempenho na Web e testes de unidade para um cenário de teste de carga](http://msdn.microsoft.com/en-us/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Como: remover testes da Web e testes de unidade de um cenário de teste de carga](http://msdn.microsoft.com/en-us/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Definição e aplicação de restrições de qualidade:** você pode criar restrições de qualidade para garantir que os testes sejam executados antes que o código seja verificado para ajudar a garantir a qualidade do código.|-   [Definição e aplicação de restrições de qualidade](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Extensão do tipo de teste de unidade:**você pode adicionar uma funcionalidade aos seus testes que pode não estar no framework de teste de unidade. Por exemplo, é possível adicionar uma propriedade de teste que especifica se um teste deve ser executado como um usuário normal ou não. Ou você pode estender a estrutura para adicionar atributos de linha a um método e usar os dados nessa linha dentro do teste.|Para o código de exemplo de como estender o framework de teste de unidade, confira este [Site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Definição de opções de teste:** por exemplo, você pode especificar onde os resultados dos testes são armazenados.|[Configurar testes de unidade usando um arquivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Tarefas relacionadas  
 [Revisão dos resultados de testes no Microsoft Test Manager](http://msdn.microsoft.com/en-us/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Descreve os resultados dos testes e as maneiras de trabalhar com eles, incluindo como exibi-los, salvá-los e excluí-los.  
  
 [Execução dos testes de sistema usando o Microsoft Visual Studio](/devops-test-docs/test/running-automated-tests-using-microsoft-visual-studio)  
  
 Fornece links para informações sobre o uso do Visual Studio em vez de usar o [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] para executar testes automatizados.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Descreve o namespace UnitTesting, que fornece atributos, exceções, asserções e outras classes que oferecem suporte a testes de unidade.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Descreve o namespace UnitTesting.Web, que estende o namespace UnitTesting fornecendo suporte para o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e a testes de unidade do serviço Web.  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="videos"></a>Vídeos  
 [Canal 9: teste de unidade dos aplicativos da Windows Store criados com XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Fóruns  
 [Teste de unidade do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Diretrizes  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Testando para entrega contínua com o Visual Studio 2012 – Capítulo 2: Teste de unidade: testando o interior)  
  
### <a name="reference"></a>Referência  
 [Índice de conteúdo para testes de unidade](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Consulte também  
 [Melhorar a Qualidade do Código](http://msdn.microsoft.com/Library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Testando o aplicativo](/devops-test-docs/test/test-apps-early-and-often)

