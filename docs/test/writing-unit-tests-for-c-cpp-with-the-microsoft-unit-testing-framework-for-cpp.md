---
title: "Escrevendo testes de unidade para C-c + + com o Microsoft Unit Testing Framework para C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "mlearned"
manager: "douge"
---
# Escrevendo teste de unidade para C/C++ com o Microsoft Unit Testing Framework para C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No Visual Studio, você pode criar testes de unidade para código não gerenciado escrito em C++. Código não gerenciado é às vezes chamado de código nativo.  
  
 O procedimento a seguir contém as informações essenciais que é iniciado. As seções posteriores fornecem uma explicação passo a passo que descreve as etapas mais detalhadamente.  
  
### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Para escrever testes de unidade para uma DLL de código não gerenciado  
  
1.  Use o **nativo Test Project** modelo para criar um projeto separado do Visual Studio para os testes.  
  
     O projeto contém alguns exemplos de código de teste.  
  
2.  Disponibilize a DLL para o projeto de teste:  
  
    -   `#include` um `.h` arquivo que contém as declarações das funções da DLL acessíveis externamente.  
  
         O `.h` arquivo deve conter declarações de função marcadas com `_declspec(dllimport)`. Como alternativa, você pode exportar os métodos usando um arquivo de Definição. Para obter mais informações, consulte [Importando e exportando](/visual-cpp/build/importing-and-exporting).  
  
         Os testes de unidade podem acessar apenas as funções exportadas da DLL em teste.  
  
    -   Adicione o projeto DLL às referências do projeto de teste:  
  
         No **propriedades** do projeto de teste, expanda **Propriedades comuns**, **estrutura e referências**, e escolha **Adicionar referência**.  
  
3.  No projeto de teste, crie classes de teste e métodos de teste usando as macros de TESTE e a classe Assert da seguinte maneira:  
  
    ```cpp  
    #include "stdafx.h"  
    #include <CppUnitTest.h>  
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    TEST_CLASS(TestClassName)  
    {  
    public:  
      TEST_METHOD(TestMethodName)  
      {  
        // Run a function under test here.  
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());  
      }  
    }  
    ```  
  
    -   `Assert` contém várias funções estáticas que você pode usar para verificar o resultado de um teste.  
  
    -   O `LINE_INFO()` parâmetro é opcional. Em casos onde não há nenhum arquivo PDB, ele permite que o executor de teste identificar o local de uma falha.  
  
    -   Você também pode escrever métodos de instalação e limpeza de teste. Para obter mais informações, abra a definição do `TEST_METHOD` macro e ler os comentários no CppUnitTest.h  
  
    -   Não é possível aninhar as classes de teste.  
  
4.  Use o Gerenciador de testes para executar os testes:  
  
    1.  Sobre o **exibição** menu, escolha **outras janelas**, **Test Explorer**.  
  
    2.  Compile a solução do Visual Studio.  
  
    3.  No Gerenciador de testes, escolha **Executar tudo**.  
  
    4.  Para investigar qualquer teste em mais detalhes no Gerenciador de testes:  
  
        1.  Selecione o nome do teste para ver mais detalhes, como um rastreamento de mensagens e pilha de falha.  
  
        2.  Abra o nome do teste (por exemplo clicando duas vezes) para ir para o local de falha ou para o código de teste.  
  
        3.  No menu de atalho para um teste, escolha **Depurar selecionado testar** para executar o teste no depurador.  
  
##  <a name="a-namewalkthrougha-walkthrough-developing-an-unmanaged-dll-with-test-explorer"></a><a name="walkthrough"></a> Passo a passo: Desenvolvendo uma DLL não gerenciada com o Gerenciador de testes  
 Você pode adaptar este passo a passo para desenvolver sua própria DLL. As etapas principais são os seguintes:  
  
1.  [Criar um projeto de teste nativo](#unitTestProject). Os testes são criados em um projeto separado da DLL que você está desenvolvendo.  
  
2.  [Criar um projeto de DLL](#createDllProject). Este passo a passo cria uma nova DLL, mas o procedimento para testar uma DLL existente é semelhante.  
  
3.  [Tornar as funções DLL visível para os testes](#coupleProjects).  
  
4.  [Aumente interativamente os testes](#iterate). É recomendável um ciclo "vermelho-verde-refatoração", em que o desenvolvimento do código é organizado pelos testes.  
  
5.  [Depurar testes com falha](#debug). Você pode executar testes no modo de depuração.  
  
6.  [Refatorar manter os testes inalterada](#refactor). Refatoração significa melhorando a estrutura do código sem alterar o comportamento externo. Você pode fazer para melhorar o desempenho, a extensibilidade ou a legibilidade do código. Porque a intenção é não alterar o comportamento, você não altere os testes ao fazer uma alteração de refatoração de código. Os testes de ajudam a garantir que não apresenta erros enquanto você estiver refatoração. Portanto, você pode fazer essas alterações com muito mais confiança que se você não tinha os testes.  
  
7.  [Verificar a cobertura de](https://msdn.microsoft.com/en-us/library/fc8hec9e.aspx). Testes de unidade são mais úteis quando eles testam mais do seu código. Você pode descobrir quais partes do seu código foram usadas pelos testes.  
  
8.  [Isolar unidades de recursos externos](https://msdn.microsoft.com/library/hh549174.aspx). Normalmente, uma DLL é dependente de outros componentes do sistema que você está desenvolvendo, como outras DLLs, bancos de dados ou subsistemas remotos. É útil testar cada unidade em isolamento de suas dependências. Componentes externos podem fazer testes sejam executados lentamente. Durante o desenvolvimento, os outros componentes não podem ser concluídos.  
  
###  <a name="a-nameunittestprojecta-create-a-native-unit-test-project"></a><a name="unitTestProject"></a> Criar um projeto de teste de unidade nativo  
  
1.  Sobre o **arquivo** menu, escolha **novo**, **projeto**.  
  
     Na caixa de diálogo, expanda **instalados**, **modelos**, **Visual C++**, **teste**.  
  
     Escolha o **nativo Test Project** modelo.  
  
     Neste passo a passo, o projeto de teste é denominado `NativeRooterTest`.  
  
     ![Criando uma C &#43; &#43; Projeto de teste de unidade](../test/media/utecpp01.png "UteCpp01")  
  
2.  No novo projeto, inspecionar **unittest1.cpp**  
  
     ![Testar o projeto com TEST &#95; CLASSE de TESTE e #95; MÉTODO](../test/media/utecpp2.png "UteCpp2")  
  
     Observe que:  
  
    -   Cada teste é definido usando `TEST_METHOD(YourTestName){...}`.  
  
         Você não precisa escrever uma assinatura de função convencional. A assinatura é criada pela macro TEST_METHOD. A macro gera uma função de instância que retorna void. Também gera uma função estática que retorna informações sobre o método de teste. Essas informações permitem que o Gerenciador de testes localizar o método.  
  
    -   Métodos de teste são agrupados em classes usando `TEST_CLASS(YourClassName){...}`.  
  
         Quando os testes são executados, uma instância de cada classe de teste é criada. Os métodos de teste são chamados em uma ordem não especificada. Você pode definir métodos especiais que são invocados antes e depois de cada módulo, classe ou método.  
  
3.  Verifique se os testes executados no Gerenciador de testes:  
  
    1.  Insira algum código de teste:  
  
        ```cpp  
        TEST_METHOD(TestMethod1)  
        {  
        Assert::AreEqual(1,1);  
        }  
        ```  
  
         Observe que a classe `Assert` fornece vários métodos estáticos que você pode usar para verificar os resultados em métodos de teste.  
  
    2.  Sobre o **teste** menu, escolha **executar** , **todos os testes**.  
  
         O teste compilado e executado.  
  
         O Gerenciador de testes é exibida.  
  
         O teste aparece sob **testes aprovados**.  
  
         ![Gerenciador de testes de unidade com um teste passado](../test/media/utecpp04.png "UteCpp04")  
  
###  <a name="a-namecreatedllprojecta-create-an-unmanaged-dll-project"></a><a name="createDllProject"></a> Criar um projeto de DLL não gerenciada  
  
1.  Criar um **Visual C++** projeto usando o **Win32 Project** modelo.  
  
     Neste passo a passo, o projeto é denominado `RootFinder`.  
  
     ![Criando uma C &#43; &#43; Projeto Win32](../test/media/utecpp05.png "UteCpp05")  
  
2.  Selecione **DLL** e **exportar símbolos** no Assistente de aplicativo Win32.  
  
     O **exportar símbolos** opção gera uma macro conveniente que você pode usar para declarar métodos exportados.  
  
     ![C &#43; &#43; Assistente de projeto do conjunto de DLL e exportar símbolos](../test/media/utecpp06.png "UteCpp06")  
  
3.  Declare uma função exportada no arquivo. h principal:  
  
     ![Novo código de projeto e. h arquivo DLL com macros de API](../test/media/utecpp07.png "UteCpp07")  
  
     O declarador `__declspec(dllexport)` faz com que os membros públicos e protegidos da classe seja visível fora da DLL. Para obter mais informações, consulte [usando dllimport e dllexport em Classes C++](/visual-cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).  
  
4.  No arquivo. cpp principal, adicione um corpo mínimo para a função:  
  
    ```cpp  
    // Find the square root of a number.  
    double CRootFinder::SquareRoot(double v)  
    {  
      return 0.0;  
    }  
    ```  
  
###  <a name="a-namecoupleprojectsa-couple-the-test-project-to-the-dll-project"></a><a name="coupleProjects"></a> Acoplar o projeto de teste para o projeto DLL  
  
1.  Adicione o projeto DLL às referências do projeto do projeto de teste:  
  
    1.  Abra as propriedades do projeto de teste e escolha **Propriedades comuns**, **estrutura e referências**.  
  
         ![C &#43; &#43; Propriedades do projeto e 45; Estrutura e referências](../test/media/utecpp08.png "UteCpp08")  
  
    2.  Escolha **Adicionar nova referência**.  
  
         Na **Adicionar referência** caixa de diálogo Selecione o projeto DLL e escolha **Adicionar**.  
  
         ![C &#43; &#43; Propriedades do projeto e 45; Adicionar nova referência](../test/media/utecpp09.png "UteCpp09")  
  
2.  No arquivo. cpp de teste de unidade principal, inclua o arquivo. h do código de DLL:  
  
    ```cpp  
    #include "..\RootFinder\RootFinder.h"  
    ```  
  
3.  Adicione um teste básico que usa a função exportada:  
  
    ```cpp  
    TEST_METHOD(BasicTest)  
    {  
    CRootFinder rooter;  
    Assert::AreEqual(  
    // Expected value:  
    0.0,   
    // Actual value:  
    rooter.SquareRoot(0.0),   
    // Tolerance:  
    0.01,  
    // Message:  
    L"Basic test failed",  
    // Line number - used if there is no PDB file:  
    LINE_INFO());  
    }  
    ```  
  
4.  Compile a solução.  
  
     O novo teste aparece no Gerenciador de testes.  
  
5.  No Gerenciador de testes, escolha **Executar tudo**.  
  
     ![Gerenciador de testes de unidade &45; Teste básico passado](../test/media/utecpp10.png "UteCpp10")  
  
 Você configurou o teste e os projetos de código, além de ter verificado que pode executar testes que executam funções no projeto de código. Agora, você pode começar a escrever testes e códigos reais.  
  
###  <a name="a-nameiteratea-iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Aumente os testes e torná-los transmitir iterativamente  
  
1.  Adicione um novo teste:  
  
    ```cpp  
    TEST_METHOD(RangeTest)  
    {  
      CRootFinder rooter;  
      for (double v = 1e-6; v < 1e6; v = v * 3.2)  
      {  
        double actual = rooter.SquareRoot(v*v);  
        Assert::AreEqual(v, actual, v/1000);  
      }  
    }  
    ```  
  
    > [!TIP]
    >  É recomendável não alterar testes que tenham sido aprovados. Em vez disso, adicione um novo teste, atualize o código para que o teste seja aprovado e adicione outro teste, e assim por diante.  
    >   
    >  Quando os usuários alterarem os respectivos requisitos, desabilite os testes que não estejam mais corretos. Escreva novos testes e faça-os funcionar, um por vez, da mesma maneira incremental.  
  
2.  Crie a solução e, em seguida, no Gerenciador de testes, escolha **Executar tudo**.  
  
     O novo teste falha.  
  
     ![A falha de RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Verifique se que cada teste falhará imediatamente depois que você escreveu. Isso ajuda a impedir a facilidade de errar ao escrever um teste que nunca falha.  
  
3.  Aprimorar o código em teste para que o novo teste é aprovado:  
  
    ```cpp  
    #include <math.h>  
    ...  
    double CRootFinder::SquareRoot(double v)  
    {  
      double result = v;  
      double diff = v;  
      while (diff > result/1000)  
      {  
        double oldResult = result;  
        result = result - (result*result - v)/(2*result);  
        diff = abs (oldResult - result);  
      }  
      return result;  
    }  
    ```  
  
4.  Crie a solução e, em seguida, no Gerenciador de testes, escolha **Executar tudo**.  
  
     Ambos os testes forem aprovados.  
  
     ![Gerenciador de testes de unidade e 45; Intervalo de teste foi aprovado](../test/media/utecpp12.png "UteCpp12")  
  
    > [!TIP]
    >  Desenvolva o código adicionando testes, um de cada vez. Verifique se todos os testes passaram após cada iteração.  
  
###  <a name="a-namedebuga-debug-a-failing-test"></a><a name="debug"></a> Depurar um teste de falha  
  
1.  Adicione outro teste:  
  
    ```cpp  
  
    #include <stdexcept>  
    ...  
    // Verify that negative inputs throw an exception.  
    TEST_METHOD(NegativeRangeTest)  
    {  
      wchar_t message[200];  
      CRootFinder rooter;  
      for (double v = -0.1; v > -3.0; v = v - 0.5)  
      {  
        try   
        {  
          // Should raise an exception:  
          double result = rooter.SquareRoot(v);  
  
          _swprintf(message, L"No exception for input %g", v);  
          Assert::Fail(message, LINE_INFO());  
        }  
        catch (std::out_of_range ex)  
        {  
          continue; // Correct exception.  
        }  
        catch (...)  
        {  
          _swprintf(message, L"Incorrect exception for %g", v);  
          Assert::Fail(message, LINE_INFO());  
        }  
      }  
    }  
    ```  
  
2.  Crie a solução e escolha **Executar tudo**.  
  
3.  Abrir (ou clique duas vezes) no teste que falhou.  
  
     A asserção com falha é realçada. A mensagem de falha fica visível no painel de detalhes do Gerenciador de Testes.  
  
     ![Falha de NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
4.  Para ver o motivo da falha do teste, percorra a função:  
  
    1.  Defina um ponto de interrupção no início da função SquareRoot.  
  
    2.  No menu de atalho do teste com falha, escolha **Depurar testes selecionados**.  
  
         Quando a execução for interrompida no ponto de interrupção, percorra o código.  
  
5.  Insira o código na função que você está desenvolvendo:  
  
    ```cpp  
  
    #include <stdexcept>  
    ...  
    double CRootFinder::SquareRoot(double v)  
    {  
        // Validate parameter:  
        if (v < 0.0)   
        {  
          throw std::out_of_range("Can't do square roots of negatives");  
        }  
  
    ```  
  
6.  Todos os testes agora foram aprovados.  
  
     ![Todos os testes passarem](../test/media/ute_ult_alltestspass.png "UTE_ULT_AllTestsPass")  
  
> [!TIP]
>  Se os testes individuais não têm dependências que impedem que está sendo executado em qualquer ordem, ative a execução de teste em paralelo com o ![UTE &#95; parallelicon &45; pequeno](../test/media/ute_parallelicon-small.png "UTE_parallelicon-small") botão de alternância na barra de ferramentas. Isso pode reduzir consideravelmente o tempo necessário para executar todos os testes.  
  
###  <a name="a-namerefactora-refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Refatorar o código sem alterar os testes  
  
1.  Simplificar o cálculo central na função SquareRoot:  
  
    ```  
    // old code:  
    //   result = result - (result*result - v)/(2*result);  
    // new code:  
         result = (result + v/result)/2.0;  
  
    ```  
  
2.  Crie a solução e escolha **Executar todos**, para certificar-se de que você não introduziu um erro.  
  
    > [!TIP]
    >  Um bom conjunto de testes de unidade permite que você não introduziu bugs quando você alterar o código de confiança.  
    >   
    >  Manter refatoração separadas de outras alterações.  
  
## <a name="next-steps"></a>Próximas etapas  
  
-   **Isolamento.** A maioria das DLLs são outros subsistemas, como bancos de dados e outras DLLs dependentes. Geralmente, esses outros componentes são desenvolvidos em paralelo. Para permitir que os testes de unidade para ser executada enquanto os outros componentes ainda não estão disponíveis, você precisa substituir mock ou  
  
-   **Crie testes de verificação.** Você pode fazer testes executados no servidor de compilação da equipe em intervalos definidos. Isso garante que os erros não são introduzidos quando o trabalho de vários membros da equipe é integrado.  
  
-   **Testes de check-in.** Você pode obrigar que alguns testes são executadas antes de cada membro da equipe verifica o código no controle de origem. Normalmente, esse é um subconjunto do conjunto completo de testes de verificação de compilação.  
  
     Você também pode designar um nível mínimo de cobertura de código.  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando testes de unidade para aplicativos do C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)   
 [Usando Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)   
 [Uma visão geral da interoperabilidade entre código gerenciado /](http://msdn.microsoft.com/library/ms973872.aspx)   
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Passo a passo: Criando e usando uma biblioteca de vínculo dinâmico (C++)](../Topic/Walkthrough:%20Creating%20and%20Using%20a%20Dynamic%20Link%20Library%20\(C++\).md)   
 [Importando e exportando](/visual-cpp/build/importing-and-exporting)