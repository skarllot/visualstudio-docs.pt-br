---
title: "No&#231;&#245;es b&#225;sicas de teste de unidade | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UnitTest.CreateUnitTest"
ms.assetid: a80ba9cd-4575-483c-b957-af7ed8dc7e20
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "mlearned"
manager: "douge"
---
# No&#231;&#245;es b&#225;sicas de teste de unidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verifique se seu código está funcionando conforme o esperado, criando e executando testes de unidade. Ele é chamado porque você separar a funcionalidade de seu programa em comportamentos testáveis discretos que você pode testar como individuais de testes de unidade *unidades*. Visual Studio Test Explorer fornece uma maneira flexível e eficiente para executar seus testes de unidade e exibir seus resultados no Visual Studio. Visual Studio instala estruturas para código gerenciado e nativo de testes de unidade de Microsoft. Use um *estrutura de teste de unidade* para criar testes de unidade, executá\-los e relatar os resultados desses testes. Testes de unidade de executar novamente quando você fizer alterações para testar seu código ainda está funcionando corretamente. Quando você usa o Visual Studio Enterprise, você pode executar testes automaticamente após cada compilação.  
  
 Teste de unidade tem o maior efeito sobre a qualidade do seu código quando ele é parte integrante de seu fluxo de trabalho de desenvolvimento de software. Assim que você escrever uma função ou outro bloco de código do aplicativo, crie testes de unidade que verifique o comportamento do código em resposta a standard, limites e casos incorretos de dados de entrada e que nenhuma suposição explícita ou implícita feita pelo código. Com *desenvolvimento orientado por testes*, criar testes de unidade antes de escrever o código para usar os testes de unidade como documentação de design e especificações funcionais.  
  
 Você pode gerar rapidamente os projetos de teste e métodos de teste do seu código ou criar manualmente os testes conforme necessário. Quando você usar o IntelliTest para explorar seu código .NET, você pode gerar dados de teste e um conjunto de testes de unidade. Para cada instrução no código, é gerada uma entrada de teste que executar essa instrução. Descubra como [Gerar testes de unidade para código](http://msdn.microsoft.com/library/dn823749.aspx).  
  
 O Gerenciador de testes também pode executar código aberto e de terceiros estruturas de teste de unidade que implementaram interfaces de complemento do Gerenciador de testes. Você pode adicionar muitas dessas estruturas por meio do Gerenciador de extensões do Visual Studio e a Galeria do Visual Studio. Consulte [Instalar estruturas de teste de unidade de terceiros](../test/install-third-party-unit-test-frameworks.md).  
  
-   [Início rápido](#BKMK_Quick_starts)  
  
-   [O exemplo de solução de MyBank](#BKMK_The_MyBank_Solution_example)  
  
-   [Criar projetos de teste de unidade e métodos de teste](#BKMK_Creating_the_unit_test_projects)  
  
-   [Escrever seus testes](#BKMK_Writing_your_tests)  
  
-   [Executar testes no Gerenciador de testes](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [Executar e exibir testes](#BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar)  
  
##  <a name="BKMK_Unit_testing_overview"></a> Visão geral de teste de unidade  
  
###  <a name="BKMK_Quick_starts"></a> Início rápido  
 Para obter uma introdução ao teste de unidade que leva você diretamente em codificação, consulte um destes tópicos:  
  
-   [Instruções passo a passo: criando e executando testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)  
  
-   [Início rápido: desenvolvimento baseado em testes com o Gerenciador de Testes](../test/quick-start-test-driven-development-with-test-explorer.md)  
  
-   [Teste o código nativo com o Gerenciador de testes de unidade](http://msdn.microsoft.com/pt-br/8a09d6d8-3613-49d8-9ffe-11375ac4736c)  
  
##  <a name="BKMK_The_MyBank_Solution_example"></a> O exemplo de solução de MyBank  
 Neste tópico, usamos o desenvolvimento de um aplicativo fictício chamado `MyBank` como exemplo. Não é necessário o código real que siga as explicações neste tópico. Métodos de teste são escritos em c\# e apresentados usando o Microsoft Unit Testing Framework para código gerenciado, no entanto, os conceitos são facilmente transferidos para outros idiomas e estruturas.  
  
 ![Solução de MyBank](../test/media/ute_mybanksolution.png "UTE\_MyBankSolution")  
  
 Nossa primeira tentativa de um projeto para a `MyBank` aplicativo inclui um componente de contas que representa uma conta individual e suas transações com o banco e um componente de banco de dados que representa a funcionalidade de agregação e gerenciar as contas individuais.  
  
 Criamos um `MyBank` solução que contém dois projetos:  
  
-   `Accounts`  
  
-   `BankDb`  
  
 Nossa primeira tentativa de criação de `Accounts` projeto contém uma classe para manter informações básicas sobre uma conta, uma interface que especifica a funcionalidade comum de qualquer tipo de conta, como depositando e retirando ativos da conta, e uma classe derivada da interface que representa uma conta bancária. Começamos os projetos de contas, criando os seguintes arquivos de origem:  
  
-   `AccountInfo.cs` Define as informações básicas para uma conta.  
  
-   `IAccount.cs` define um padrão `IAccount` interface para uma conta, incluindo métodos de depósito e retirar ativos de uma conta e recuperar o saldo da conta.  
  
-   `CheckingAccount.cs` contém o `CheckingAccount` classe que implementa o `IAccounts` interface para uma conta bancária.  
  
 Sabemos de experiência que uma coisa que deve fazer uma retirada de uma conta bancária certificar\-se de que a quantidade retirada é menor que o saldo da conta. Podemos substituirão o `IAccount.Withdaw` método `CheckingAccount` com um método que verifica para essa condição. O método pode ter esta aparência:  
  
```c#  
  
public void Withdraw(double amount)  
{  
    if(m_balance >= amount)  
    {  
        m_balance -= amount;  
    }  
    else  
    {  
        throw new ArgumentException(amount, "Withdrawal exceeds balance!")  
    }  
}  
  
```  
  
 Agora que temos alguns códigos, é hora de testar.  
  
##  <a name="BKMK_Creating_the_unit_test_projects"></a> Criar projetos de teste de unidade e métodos de teste  
 Geralmente é mais rápido gerar o projeto de teste de unidade e stubs de teste de unidade no seu código. Ou você pode optar por criar o projeto de teste de unidade e testes manualmente dependendo dos seus requisitos.  
  
 **Gerar o projeto de teste de unidade e stubs de teste de unidade**  
  
1.  Na janela do editor de código, clique com botão direito e escolha **Create Unit Tests** no menu de contexto.  
  
     ![From the editor window, view the context menu](../test/media/createunittestsrightclick.png "CreateUnitTestsRightClick")  
  
2.  Clique em OK para aceitar os padrões para criar testes de unidade, ou alterar os valores usados para criar e teste de nome de unidade de projeto e os testes de unidade. Você pode selecionar o código que é adicionado por padrão para os métodos de teste de unidade.  
  
     ![Right&#45;click in editor and choose Create Unit Tests](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")  
  
3.  Os stubs de teste de unidade são criados em um novo projeto de teste de unidade para todos os métodos na classe.  
  
     ![The unit tests are created](../test/media/createunittestsstubs.png "CreateUnitTestsStubs")  
  
4.  Agora, pule para saber como [Adicionar código para os métodos de teste de unidade](#BKMK_Writing_your_tests) para fazer o teste de unidade significativo e quaisquer testes de unidade extra que você talvez queira adicionar para testar seu código.  
  
 **Criar testes de unidade e de projeto de seu teste de unidade manualmente**  
  
 Um projeto de teste de unidade geralmente espelha a estrutura de um projeto de código única. O exemplo de MyBank, você adicionará dois projetos de teste de unidade chamados `AccountsTests` e `BankDbTests` para o `MyBanks` solução. Os nomes de projeto de teste são arbitrários, mas adotar uma convenção de nomenclatura padrão é uma boa idéia.  
  
 **Para adicionar um projeto de teste de unidade para uma solução:**  
  
1.  Sobre o **arquivo** menu, escolha **novo** e, em seguida, escolha **projeto** \(teclado: Ctrl \+ Shift \+ N\).  
  
2.  Na caixa de diálogo Novo projeto, expanda o **instalados** nó, escolha o idioma que você deseja usar para o seu projeto de teste e escolha **teste**.  
  
3.  Para usar uma das estruturas de teste de unidade do Microsoft, escolha **o projeto de teste de unidade** da lista de modelos de projeto. Caso contrário, escolha o modelo de projeto da unidade do framework de teste que você deseja usar. Para testar o `Accounts` projeto do nosso exemplo, você deve nomear o projeto `AccountsTests`.  
  
    > [!WARNING]
    >  Nem todas as estruturas de teste de unidade de código aberto e de terceiros fornecem um modelo de projeto do Visual Studio. Consulte o documento do framework para obter informações sobre como criar um projeto.  
  
4.  Em seu projeto de teste de unidade, adicione uma referência ao projeto de código em teste, em nosso exemplo para o projeto de contas.  
  
     Para criar a referência ao projeto de código:  
  
    1.  Selecione o projeto no Solution Explorer.  
  
    2.  Sobre o **projeto** menu, escolha **Adicionar referência**.  
  
    3.  Na caixa de diálogo Gerenciador de referência, abra o **solução** nó e escolha **projetos**. Selecione o nome do projeto de código e feche a caixa de diálogo.  
  
 Cada projeto de teste de unidade contém classes que refletem os nomes das classes no código do projeto. Em nosso exemplo, o `AccountsTests` projeto contém as seguintes classes:  
  
-   `AccountInfoTests` classe contém os métodos de teste de unidade para o `AccountInfo` classe o `BankAccount` projeto  
  
-   `CheckingAccountTests` classe contém os métodos de teste de unidade para `CheckingAccount` classe.  
  
##  <a name="BKMK_Writing_your_tests"></a> Escrever seus testes  
 O teste de unidade do framework que você usa e o Visual Studio IntelliSense para guiá\-lo por meio de escrever o código para os testes de unidade para um projeto de código. Para executar no Gerenciador de testes, a maioria das estruturas exigem que você adicione atributos específicos para identificar os métodos de teste de unidade. As estruturas também fornecem uma maneira — geralmente por meio de declarar declarações ou atributos de método — para indicar se o método de teste passou ou falhou. Outros atributos identificam os métodos de instalação opcional na classe de inicialização e antes de cada método de teste e métodos de subdivisão que serão executados após cada método de teste e antes que a classe seja destruída.  
  
 O padrão AAA \(Arrange, Act, Assert\) é uma maneira comum de escrever testes de unidade para um método em teste.  
  
-   O **Organizar** seção de um método de teste de unidade inicializa os objetos e define o valor dos dados que são passados para o método sendo testado.  
  
-   O **Act** seção invoca o método sendo testado com os parâmetros organizados.  
  
-   O **Assert** seção verifica se a ação do método em teste se comporta conforme o esperado.  
  
 Para testar o `CheckingAccount.Withdraw` método de nosso exemplo, podemos escrever dois testes: um que verifica o comportamento padrão do método e que verifica se uma retirada de mais do que o saldo falhará. Na `CheckingAccountTests` classe, podemos adicionar métodos a seguir:  
  
```c#  
[TestMethod]  
public void Withdraw_ValidAmount_ChangesBalance()  
{  
    // arrange  
    double currentBalance = 10.0;  
    double withdrawal = 1.0;  
    double expected = 9.0;  
    var account = new CheckingAccount("JohnDoe", currentBalance);  
    // act  
    account.Withdraw(withdrawal);  
    double actual = account.Balance;  
    // assert  
    Assert.AreEqual(expected, actual);  
}  
  
[TestMethod]  
[ExpectedException(typeof(ArgumentException))]  
public void Withdraw_AmountMoreThanBalance_Throws()  
{  
    // arrange  
    var account = new CheckingAccount("John Doe", 10.0);  
    // act  
    account.Withdraw(20.0);  
    // assert is handled by the ExpectedException  
}  
  
```  
  
 Observe que `Withdraw_ValidAmount_ChangesBalance` usa explícito `Assert` instrução para determinar se o método de teste é aprovado ou reprovado, enquanto `Withdraw_AmountMoreThanBalance_Throws` usa o `ExpectedException` atributo para determinar o êxito do método de teste. Nos bastidores, uma estrutura de teste de unidade encapsula os métodos de teste em instruções try\/catch. Na maioria dos casos, se uma exceção é detectada, o método de teste falhará e a exceção será ignorada. O `ExpectedException` atributo faz com que o método de teste passar se a exceção especificada.  
  
 Para obter mais informações sobre as estruturas de testes de unidade da Microsoft, consulte um dos seguintes tópicos:  
  
-   [Escrevendo testes de unidade para .NET Framework com o Microsoft Unit Test Framework para código gerenciado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Escrevendo testes de unidade para C\/C\+\+ com o Microsoft Unit Testing Framework para C\+\+](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
## Definir tempos limite para testes de unidade  
 Para definir um tempo limite em um método de teste individual:  
  
```c#  
[TestMethod]  
[Timeout(2000)]  // Milliseconds  
public void My_Test()  
{ ...  
}  
```  
  
```vb  
  
```  
  
 Para definir o tempo limite para o máximo permitido:  
  
```c#  
[TestMethod]  
[Timeout(TestTimeout.Infinite)]  // Milliseconds  
public void My_Test ()  
{ ...  
}  
```  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Executar testes no Gerenciador de testes  
 Quando você compila o projeto de teste, os testes são exibidos no Gerenciador de testes. Se o Gerenciador de testes não estiver visível, escolha **teste** no menu do Visual Studio, escolha **Windows**, e, em seguida, escolha **Test Explorer**.  
  
 ![Explorer de teste de unidade](../ide/media/ute_failedpassednotrunsummary.png "UTE\_FailedPassedNotRunSummary")  
  
 Como executar, gravar e executar novamente os testes, a exibição padrão do Gerenciador de testes exibe os resultados em grupos de **testes com falha**, **testes aprovados**, **testes ignorada** e **Not Run Tests**. Você pode escolher um cabeçalho de grupo para abrir o modo de exibição exibe todos os testes no grupo.  
  
 Você também pode filtrar os testes em qualquer modo, o texto correspondente na caixa de pesquisa no nível global ou selecionando um dos filtros predefinidos. Você pode executar qualquer seleção de testes a qualquer momento. Os resultados de uma execução de teste são imediatamente aparentes na barra de aprovação ou reprovação na parte superior da janela do explorer. Detalhes do resultado de um método de teste são exibidos quando você seleciona o teste.  
  
###  <a name="BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar"></a> Executar e exibir testes  
 A barra de ferramentas do Gerenciador de testes ajuda a descobrir, organizar e executar os testes que você está interessado.  
  
 ![Executar testes da barra de ferramentas Test Explorer](../test/media/ute_toolbar.png "UTE\_ToolBar")  
  
 Você pode escolher **Executar todos** para executar todos os testes, ou **executar** para escolher um subconjunto de testes a serem executados. Depois de executar um conjunto de testes, um resumo da execução do teste é exibido na parte inferior da janela do Gerenciador de testes. Selecione um teste para exibir os detalhes desse teste no painel inferior. Escolha **Abrir teste** no menu de contexto \(teclado: F12\) para exibir o código\-fonte para o teste selecionado.  
  
 Se os testes individuais não têm dependências que impedem que está sendo executado em qualquer ordem, ative a execução de teste em paralelo com o ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE\_parallelicon\-small") botão de alternância na barra de ferramentas. Isso pode reduzir consideravelmente o tempo necessário para executar todos os testes.  
  
###  <a name="BKMK_Running_tests_after_every_build"></a> Executar testes após cada compilação  
  
> [!WARNING]
>  Executando testes de unidade após cada compilação é suportada apenas no Visual Studio Enterprise.  
  
|||  
|-|-|  
|![Run after build](../test/media/ute_runafterbuild_btn.png "UTE\_RunAfterBuild\_btn")|Para executar os testes de unidade após cada compilação local, escolha **teste** no menu padrão, escolha **executar testes após compilação** na barra de ferramentas do Gerenciador de testes.|  
  
###  <a name="BKMK_Filtering_and_grouping_the_test_list"></a> Filtrar e agrupar a lista de teste  
 Quando você tiver um grande número de testes, você pode digitar na caixa de pesquisa do Gerenciador de testes para filtrar a lista por cadeia de caracteres especificada. Você pode restringir seu evento de filtro mais escolhendo na lista de filtros.  
  
 ![Categorias de filtro de pesquisa](../test/media/ute_searchfilter.png "UTE\_SearchFilter")  
  
|||  
|-|-|  
|![Botão de teste do grupo Explorer](../test/media/ute_groupby_btn.png "UTE\_GroupBy\_btn")|Para agrupar testes por categoria, escolha o **Group By** botão.|  
  
 Para obter mais informações, consulte [Executar testes de unidade com o Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md).  
  
## PERGUNTAS E RESPOSTAS  
 **P: como posso depurar testes de unidade?**  
  
 **R:** Gerenciador de testes de uso para iniciar uma sessão de depuração para os testes. Passar pelo código com o depurador do Visual Studio permite\-lhe navegar facilmente entre os testes de unidade e o projeto sendo testado. Para iniciar a depuração:  
  
1.  No editor do Visual Studio, defina um ponto de interrupção em um ou mais métodos de teste que deseje depurar.  
  
    > [!NOTE]
    >  Como os métodos de teste podem ser executados em qualquer ordem, defina pontos de interrupção em todos os métodos de teste que deseje depurar.  
  
2.  No Gerenciador de testes, selecione os métodos de teste e escolha **Depurar testes selecionados** no menu de atalho.  
  
 Obter mais detalhes sobre [Depurar testes de unidade](../debugger/debugging-in-visual-studio.md).  
  
 **P: se estou usando TDD, como gerar código de meus testes?**  
  
 **R:** usar o IntelliSense para gerar classes e métodos no código do seu projeto. Escrever uma instrução em um método de teste que chama a classe ou método que você deseja gerar, abra o menu do IntelliSense sob a chamada. Se a chamada é um construtor da nova classe, escolha **Gerar novo tipo** no menu e siga o Assistente para inserir a classe em seu projeto de código. Se a chamada é para um método, escolha **Gerar novo método** menu do IntelliSense.  
  
 ![Gerar método Stub Intellisense Menu](../test/media/ute_generatemethodstubintellisense.png "UTE\_GenerateMethodStubIntellisense")  
  
 **P: posso criar testes de unidade que usam vários conjuntos de dados como entrada para executar o teste?**  
  
 **R:** Sim.*Métodos de teste orientado a dados* permitem que você teste um intervalo de valores com um método de teste de unidade. Use um `DataSource` de atributo para o método de teste que especifica os dados de origem e a tabela que contém os valores de variáveis que você deseja testar.  No corpo do método, você deve atribuir os valores de linha para variáveis usando a `TestContext.DataRow[`*ColumnName*`]` indexador.  
  
> [!NOTE]
>  Esses procedimentos se aplicam somente para testar métodos que você escrever usando o Microsoft unit test framework para código gerenciado. Se você estiver usando uma estrutura diferente, consulte a documentação do framework para funcionalidade equivalente.  
  
 Por exemplo, suponha que podemos adicionar um método desnecessário para a `CheckingAccount` classe chamada `AddIntegerHelper`.`AddIntegerHelper` adiciona dois números inteiros.  
  
 Para criar um teste orientado a dados para o `AddIntegerHelper` método, primeiro criamos um banco de dados do Access chamado `AccountsTest.accdb` e uma tabela chamada `AddIntegerHelperData`. O `AddIntegerHelperData` tabela define colunas para especificar o primeiro e o segundo operando da adição e uma coluna para especificar o resultado esperado. Vamos preencher um número de linhas com valores apropriados.  
  
```c#  
  
[DataSource(  
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",   
    "AddIntegerHelperData"  
)]  
[TestMethod()]  
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()  
{  
    var target = new CheckingAccount();  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.AddIntegerHelper(x, y);  
    Assert.AreEqual(expected, actual);  
}  
  
```  
  
 O método de atributo é executada uma vez para cada linha na tabela. O Gerenciador de testes relata uma falha de teste para o método se qualquer uma das iterações falharem. O painel de detalhes de resultados de teste para o método mostra o método de status de aprovação ou reprovação para cada linha de dados.  
  
 Saiba mais sobre [testes de unidade orientados a dados](../test/how-to-create-a-data-driven-unit-test.md).  
  
 **P: posso exibir quanto do meu código é testado por meus testes de unidade?**  
  
 **R:** Sim. Você pode determinar a quantidade de código que realmente está sendo testado por seus testes de unidade usando a ferramenta de cobertura de código do Visual Studio. Há suporte para idiomas nativos e gerenciados e todas as estruturas de teste de unidade que podem ser executadas pela estrutura de teste de unidade.  
  
 Você pode executar a cobertura de código em testes selecionados ou em todos os testes em uma solução. A janela Code Coverage Results exibe a porcentagem dos blocos que foram exercidos por linha, função, classe, namespace e módulo de código do produto.  
  
 Para executar a cobertura de código para métodos de teste em uma solução, escolha **testes** no menu do Visual Studio e, em seguida, escolha **Analisar cobertura de código**.  
  
 Resultados da cobertura aparecem na janela Code Coverage Results.  
  
 ![Code coverage results](../test/media/ute_codecoverageresults.png "UTE\_CodeCoverageResults")  
  
 Saiba mais sobre [cobertura de código](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .  
  
 **P: como posso testar métodos no meu código que possuem dependências externas?**  
  
 **R:** Sim. Se você tiver o Visual Studio Enterprise, Microsoft Fakes pode ser usado com métodos de teste que você escrever usando estruturas de teste de unidade para código gerenciado.  
  
 Microsoft Fakes usa duas abordagens para criar classes de substituto para as dependências externas.  
  
1.  *Stubs* gerar classes substituto derivadas da interface pai da classe de dependência de destino. Métodos stub podem substituir métodos virtuais públicos da classe de destino.  
  
2.  *Correções* usa a instrumentação de tempo de execução para desviar as chamadas para um método de destino para um método de correção de substituto para métodos não virtuais.  
  
 Em ambas as abordagens, você pode usar os delegados gerados de chamadas para o método de dependência para especificar o comportamento desejado no método de teste.  
  
 Saiba mais sobre [isolando os métodos de teste de unidade com Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
 **P: posso usar outras estruturas de teste de unidade para criar testes de unidade?**  
  
 **R:** Sim, siga estas etapas para [Localizar e instalar outras estruturas](../test/install-third-party-unit-test-frameworks.md). Depois de reiniciar o Visual Studio, reabra a solução para criar testes de unidade e selecione suas estruturas instaladas aqui:  
  
 ![Select other installed unit test framework](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")  
  
 Seu stubs de teste de unidade serão criados usando a estrutura selecionada.