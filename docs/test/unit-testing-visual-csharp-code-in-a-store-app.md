---
title: "Executar o teste de unidade de um c&#243;digo Visual C# em um aplicativo da Store | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 19
caps.handback.revision: 19
author: "alexhomer1"
ms.author: "ahomer"
manager: "robinr"
---
# Executar o teste de unidade de um c&#243;digo Visual C# em um aplicativo da Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve uma maneira de criar testes de unidade para uma classe Visual c\# em um aplicativo da Windows Store.  A classe Rooter demonstra memórias vagas da teoria de limite do cálculo implementando uma função que calcula uma estimativa da raiz quadrada de um determinado número.  O aplicativo de matemática pode usar essa função para mostrar a diversão de um usuário que pode ser feito com a matemática.  
  
 Este tópico demonstra como usar testes de unidade como a primeira etapa no desenvolvimento.  Nessa abordagem, você primeiro escreve um método de teste que verifica um comportamento específico no sistema que você está testando e, em seguida, você escreve o código que passe no teste.  Fazendo alterações na ordem dos procedimentos a seguir, você pode reverter essa estratégia para primeiro escrever o código que você deseja testar e, em seguida, escrever os testes de unidade.  
  
 Este tópico também cria uma única solução do Visual Studio e projetos separados para os testes de unidade e a DLL que você deseja testar.  Você também pode incluir os testes de unidade diretamente no projeto de DLL ou você pode criar soluções separadas para os testes de unidade e a DLL.  
  
> [!NOTE]
>  Comunidade do Visual Studio Enterprise.  e Professional fornecem recursos adicionais para testes de unidade.  
>   
>  -   Use qualquer estrutura de teste de unidade de código aberto e de terceiros que tenha criado um adaptador complementar para o Gerenciador de testes da Microsoft.  Você também pode analisar e exibir informações de cobertura de código para os testes.  
> -   Execute os testes depois de cada compilação.  
> -   VS Enterprise também contém Microsoft Fakes, uma estrutura de isolamento para código gerenciado que ajuda você a focar seus testes em seu próprio código, substituindo o código de teste para o sistema e a funcionalidade de terceiros.  
>   
>  Para obter mais informações, consulte[Verificando o código por testes de unidade usando](http://msdn.microsoft.com/library/dd264975.aspx)na biblioteca MSDN.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Criar a solução e projeto de teste de unidade](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Verificar se os testes são executados no Gerenciador de testes](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Adicionar a classe Rooter ao projeto matemática](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [Acoplar o projeto de teste ao projeto de aplicativo](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [Multiplicar os testes iterativamente e fazê-los passar](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Depurar um teste com falha](#BKMK_Debug_a_failing_test)  
  
 [Refatorar o código](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Criar a solução e projeto de teste de unidade  
  
1.  Sobre o**arquivo**menu, escolha**novo**e, em seguida, escolha**novo projeto**.  
  
2.  No**novo projeto**caixa de diálogo caixa, expanda**instalados**em seguida, expanda**Visual C\#**e escolha**da Windows Store**.  Escolha**aplicativo em branco**da lista de modelos de projeto.  
  
3.  Nomeie o projeto`matemática`e certifique\-se de**criar diretório para solução**está selecionado.  
  
4.  No Solution Explorer, escolha o nome da solução, escolha**Add**no menu de atalho e, em seguida, escolha**novo projeto**.  
  
5.  No**novo projeto**caixa de diálogo caixa, expanda**instalados**em seguida, expanda**Visual C\#**e escolha**da Windows Store**.  Escolha**biblioteca de teste de unidade \(aplicativos da Windows Store\)**da lista de modelos de projeto.  
  
     ![Criar o projeto de teste de unidade](../test/media/ute_cs_windows_createunittestproject.png "UTE\_Cs\_windows\_CreateUnitTestProject")  
  
6.  Abra Unittest1. cs no editor do Visual Studio.  
  
    ```c#  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     Observe que:  
  
    1.  Cada teste é definido usando o`[TestMethod]`.  Um método de teste deve retornar void e não pode ter nenhum parâmetro.  
  
    2.  Métodos de teste devem estar em uma classe decorada com o`[TestClass]`atributo.  
  
         Quando os testes são executados, uma instância de cada classe de teste é criada.  Os métodos de teste são chamados em uma ordem não especificada.  
  
    3.  Você pode definir métodos especiais que são chamados antes e depois de cada módulo, classe ou método.  Para obter mais informações, consulte[Usando membros do Microsoft.VisualStudio.TestTools.UnitTesting em testes de unidade](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)na biblioteca MSDN.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Verificar se os testes são executados no Gerenciador de testes  
  
1.  Insira um código de teste no`TestMethod1`do**UnitTest1.cs**arquivo:  
  
    ```c#  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Observe que o`Assert`classe fornece vários métodos estáticos que você pode usar para verificar os resultados em métodos de teste.  
  
2.  Sobre o**teste**menu, escolha**executar**e, em seguida, escolha**Executar todos**.  
  
     O projeto de teste compilado e executado.  A janela Test Explorer aparece e o teste é listado em**testes aprovados**.  O painel de resumo na parte inferior da janela fornece detalhes adicionais sobre o teste selecionado.  
  
     ![Test Explorer](../test/media/ute_cpp_testexplorer_testmethod1.png "UTE\_Cpp\_TestExplorer\_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Adicionar a classe Rooter ao projeto matemática  
  
1.  No Solution Explorer, escolha o**matemática**nome do projeto.  No menu de atalho, escolha**Add**e então**classe**.  
  
2.  Nomeie o arquivo de classe`Rooter.cs`  
  
3.  Adicione o seguinte código à classe Rooter**Rooter.cs**arquivo:  
  
    ```c#  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     O`Rooter`classe declara um construtor e o`SqareRoot`método avaliador.  
  
4.  O`SqareRoot`método é apenas uma implementação mínima, suficiente para testar a estrutura básica da configuração do teste.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Acoplar o projeto de teste ao projeto de aplicativo  
  
1.  Adicione uma referência ao aplicativo matemática para o projeto RooterTests.  
  
    1.  No Solution Explorer, escolha o**RooterTests**do projeto e escolha**Adicionar referência...**no menu de atalho.  
  
    2.  Sobre o**Adicionar referência \- RooterTests**caixa de diálogo caixa, expanda**solução**e escolha**projetos**.  Selecione o**matemática**item.  
  
         ![Adicione uma referência ao projeto matemáticas](../test/media/ute_cs_windows_addreference.png "UTE\_Cs\_windows\_AddReference")  
  
2.  Adicionar um uso a instrução para o arquivo Unittest1 CS:  
  
    1.  Abra **UnitTest1.cs**.  
  
    2.  Adicione este código abaixo do`using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;`linha:  
  
        ```c#  
        using Maths;  
        ```  
  
3.  Adicione um teste que usa a função Rooter.  Adicione o seguinte código para**UnitTest1.cpp**:  
  
    ```c#  
    [TestMethod]  
    public void BasicTest()  
    {  
        Maths.Rooter rooter = new Rooter();  
        double expected = 0.0;  
        double actual = rooter.SquareRoot(expected * expected);  
        double tolerance = .001;  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
  
    ```  
  
4.  Crie a solução.  
  
     O novo teste aparece no Gerenciador de testes no**Not Run Tests**nó.  
  
5.  No Gerenciador de Testes, escolha **Executar Tudo**.  
  
     ![Teste básico passado](../test/media/ute_cpp_testexplorer_basictest.png "UTE\_Cpp\_TestExplorer\_BasicTest")  
  
 Você configurar o teste e os projetos de código e verificar que você pode executar testes que executam funções no projeto de código.  Agora você pode começar a escrever testes e códigos reais.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Multiplicar os testes iterativamente e fazê\-los passar  
  
1.  Adicione um novo teste:  
  
    ```c#  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  É recomendável que você não altere os testes passaram.  Em vez disso, adicione um novo teste, atualize o código para que o teste seja aprovado e adicione outro teste, e assim por diante.  
    >   
    >  Quando os usuários alterarem suas necessidades, desabilite os testes que não estão mais corretos.  Escreva novos testes e fazê\-los funcionar um de cada vez, da mesma maneira incremental.  
  
2.  No Gerenciador de Testes, escolha **Executar Tudo**.  
  
3.  O teste falhará.  
  
     ![A falha de RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE\_Cpp\_TestExplorer\_RangeTest\_Fail")  
  
    > [!TIP]
    >  Logo após escrevê\-los, verifique se que cada teste falhar.  Isso ajuda a evitar a facilidade de errar ao escrever um teste que nunca falha.  
  
4.  Aprimore o código em teste para que o novo teste seja aprovado.  Alterar o`SqareRoot`funcionem em**Rooter.cs**a esta:  
  
    ```c#  
    public double SquareRoot(double x)  
    {  
        double estimate = x;  
        double diff = x;  
        while (diff > estimate / 1000)  
        {  
            double previousEstimate = estimate;  
            estimate = estimate - (estimate * estimate - x) / (2 * estimate);  
            diff = Math.Abs(previousEstimate - estimate);  
        }  
        return estimate;  
    }  
  
    ```  
  
5.  Compile a solução e, em seguida, no Gerenciador de testes, escolha**Executar todos**.  
  
     Todos os três testes agora foram aprovados.  
  
> [!TIP]
>  Desenvolva código adicionando testes, um por vez.  Certifique\-se de que todos os testes passaram após cada iteração.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Depurar um teste com falha  
  
1.  Adicione outro teste para**UnitTest1.cs**:  
  
    ```c#  
    // Verify that negative inputs throw an exception.  
    [TestMethod]  
    public void NegativeRangeTest()  
    {  
        string message;  
        Rooter rooter = new Rooter();  
        for (double v = -0.1; v > -3.0; v = v - 0.5)  
        {  
            try  
            {  
                // Should raise an exception:  
                double actual = rooter.SquareRoot(v);  
  
                message = String.Format("No exception for input {0}", v);  
                Assert.Fail(message);  
            }  
            catch (ArgumentOutOfRangeException ex)  
            {  
                continue; // Correct exception.  
            }  
            catch (Exception e)  
            {  
                message = String.Format("Incorrect exception for {0}", v);  
                Assert.Fail(message);  
            }  
        }  
    }  
  
    ```  
  
2.  No Gerenciador de Testes, escolha **Executar Tudo**.  
  
     O teste falhará.  Escolha o nome do teste no Gerenciador de testes.  Falha na asserção é realçada.  A mensagem de falha é visível no painel de detalhes do Gerenciador de testes.  
  
     ![Falha de NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE\_Cpp\_TestExplorer\_NegativeRangeTest\_Fail")  
  
3.  Para ver por que o teste falhar, percorra a função:  
  
    1.  Definir um ponto de interrupção no início de`SquareRoot`função.  
  
    2.  No menu de atalho do teste com falha, escolha**Depurar testes selecionados**.  
  
         Quando a execução for interrompida no ponto de interrupção, percorra o código.  
  
    3.  Adicione código ao método Rooter para capturar a exceção:  
  
        ```c#  
        public double SquareRoot(double x)  
        {  
            if (x < 0.0)  
            {  
                throw new ArgumentOutOfRangeException();  
        }  
  
        ```  
  
    1.  No Gerenciador de testes, escolha**Executar todos**para testar o método corrigido e certifique\-se de que você não introduziu uma regressão.  
  
 Todos os testes agora foram aprovados.  
  
 ![Passarem todos os testes](../test/media/ute_ult_alltestspass.png "UTE\_ULT\_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> Refatorar o código  
 **Simplifique o cálculo central na função SquareRoot.**  
  
1.  Alterar a implementação de resultado  
  
    ```c#  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Escolha**Executar todos**para testar o método refatorado e certifique\-se de que você não introduziu uma regressão.  
  
> [!TIP]
>  Um conjunto estável de testes de unidade permite que você não introduziu bugs quando você alterar o código de confiança.  
  
 **Refatore o código de teste para eliminar código duplicado.**  
  
 Observe que o`RangeTest`método rígido código o denominador da variável de tolerância que é usado no`Assert`método.  Se você planeja adicionar testes adicionais que usam o mesmo cálculo de tolerância a falhas, o uso de um valor embutido em vários locais pode levar a erros.  
  
1.  Adicione um método particular à classe Unit1Test para calcular o valor de tolerância e, em seguida, chame esse método.  
  
    ```c#  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  Escolha**Executar todos**para testar o método refatorado e certifique\-se de que você não introduziu um erro.  
  
> [!NOTE]
>  Para adicionar um método auxiliar para uma classe de teste, não adicione o`[TestMethod]`atributo ao método.  O Gerenciador de testes não registra o método a ser executado.