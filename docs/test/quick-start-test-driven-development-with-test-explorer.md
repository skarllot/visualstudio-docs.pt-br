---
title: "In&#237;cio r&#225;pido: desenvolvimento baseado em testes com o Gerenciador de Testes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5161b533-2127-4172-b473-d4ffc76ff05b
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "mlearned"
manager: "douge"
---
# In&#237;cio r&#225;pido: desenvolvimento baseado em testes com o Gerenciador de Testes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

É recomendável que você crie testes de unidade para ajudar a manter seu código funcionando corretamente muitas etapas incrementais de desenvolvimento. Há várias estruturas que você pode usar para escrever testes de unidade, incluindo alguns desenvolvidos por terceiros. Algumas estruturas de teste são especializadas para testes em diferentes idiomas ou plataformas. O Gerenciador de testes fornece uma interface única para testes de unidade em qualquer uma dessas estruturas. Adaptadores estão disponíveis para as estruturas comumente usada, e você pode escrever seus próprios adaptadores para outras estruturas.  
  
 O Gerenciador de testes substitui as janelas de teste de unidade encontradas em edições anteriores do Visual Studio. Suas vantagens incluem:  
  
-   Executar o .NET, não gerenciado, o banco de dados e outros tipos de testes usando uma única interface.  
  
-   Usar a estrutura de teste de unidade de sua escolha, como NUnit ou MSTest estruturas.  
  
-   Consulte todas as informações que você precisa em uma janela.  
  
## Usando o Gerenciador de testes  
 ![Executar todos os botões de exibição do Explorer de teste de unidade](../test/media/unittestexplorer-beta-.png "UnitTestExplorer\(beta\)")  
  
#### Para executar testes de unidade usando o Gerenciador de testes  
  
1.  Crie testes de unidade que usam as estruturas de teste de sua escolha.  
  
     Por exemplo, para criar um teste que usa a estrutura MSTest:  
  
    1.  Crie um projeto de teste.  
  
         No **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**, **Visual C\#**, ou **Visual C\+\+**, e, em seguida, escolha **teste**.  
  
         Selecione **projeto de teste de unidade**.  
  
    2.  Gravar cada teste de unidade como um método. Prefixo de cada método de teste com o `[TestMethod]` atributo.  
  
2.  Se os testes individuais não têm dependências que impedem que está sendo executado em qualquer ordem, ative a execução de teste em paralelo com o ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE\_parallelicon\-small") botão de alternância na barra de ferramentas. Isso pode reduzir consideravelmente o tempo necessário para executar todos os testes.  
  
3.  Na barra de menus, escolha **teste**, **executar testes de unidade**, **todos os testes**.  
  
     Criar a solução e os testes executados.  
  
     O Gerenciador de testes abre e exibe um resumo dos resultados.  
  
 **Para ver uma lista completa de testes:** escolher **Mostrar tudo** em qualquer categoria.  
  
 **Para ver os detalhes de um resultado de teste:** selecione o teste no Gerenciador de testes para exibir detalhes como mensagens de exceção no painel de detalhes.  
  
 **Para navegar até o código de um teste:** clique duas vezes o teste no Gerenciador de testes ou escolha **Abrir teste** no menu de atalho.  
  
 **Para depurar um teste:** abrir o menu de atalho para um ou mais testes e escolha **Depurar testes selecionados**.  
  
> [!IMPORTANT]
>  Os resultados são exibidos são para o mais recente executados. A barra colorida resultados mostra somente os resultados dos testes que foram executados. Por exemplo, se você executar vários testes e algumas delas falharam e execute apenas os testes com êxito, a barra de resultados mostrará todos verde.  
  
> [!NOTE]
>  Se nenhum teste seja exibido, certifique\-se de que você tenha instalado um adaptador para conectar o Gerenciador de testes para o framework de teste que você está usando. Para obter mais informações, consulte [usando diferentes estruturas de teste com o Gerenciador de testes](#frameworks).  
  
##  <a name="walkthrough"></a> Passo a passo: Usando testes de unidade para desenvolver um método  
 Este passo a passo demonstra como desenvolver um método testado em c\# usando o framework de teste de unidade da Microsoft. Você pode adaptá\-lo facilmente para outros idiomas e usar outras estruturas de teste como NUnit. Para obter mais informações, consulte [usando diferentes estruturas de teste](#frameworks).  
  
#### Criando o teste e o método  
  
1.  Crie um projeto de biblioteca de classes do Visual c\#. Esse projeto conterá o código que queremos fornecer. Neste exemplo, ele é chamado `MyMath`.  
  
2.  Crie um projeto de teste.  
  
    -   No **novo projeto** caixa de diálogo, escolha **Visual C\#**, **teste** e, em seguida, escolha **projeto de teste de unidade**.  
  
         ![Novos projetos de código e teste](../test/media/unittestexplorerwalk1.png "UnitTestExplorerWalk1")  
  
3.  Escreva um método de teste básico. Verifique se o resultado obtido de uma entrada específica:  
  
    ```c#  
  
    [TestMethod]  
    public void BasicRooterTest()  
    {  
      // Create an instance to test:  
      Rooter rooter = new Rooter();  
      // Define a test input and output value:  
      double expectedResult = 2.0;  
      double input = expectedResult * expectedResult;  
      // Run the method under test:  
      double actualResult = rooter.SquareRoot(input);  
      // Verify the result:  
      Assert.AreEqual(expectedResult, actualResult,  
          delta: expectedResult / 100);  
    }  
    ```  
  
4.  Gere o método de teste.  
  
    1.  Coloque o cursor no `Rooter`, e, em seguida, no menu de atalho, escolha **Gerar**, **novo tipo**.  
  
    2.  No **Gerar novo tipo** caixa de diálogo, defina **projeto** ao projeto de biblioteca de classes. Neste exemplo, é `MyMath`.  
  
    3.  Coloque o cursor no `SquareRoot`, e, em seguida, no menu de atalho, escolha **Gerar**, **Stub do método**.  
  
5.  Execute o teste de unidade.  
  
    1.  Sobre o **teste** menu, escolha **executar testes de unidade**, **todos os testes**.  
  
         A solução é compilado e executado.  
  
         O Gerenciador de testes abre e exibe os resultados.  
  
         O teste aparece sob **testes com falha**.  
  
6.  Selecione o nome do teste.  
  
     Os detalhes do teste são exibidos na parte inferior do Gerenciador de testes.  
  
7.  Selecione os itens em **rastreamento de pilha** para ver onde o teste falhou.  
  
 ![Teste de unidade Test Explorer mostrando falhou.](../test/media/unittestexplorerwalkthrough2.png "UnitTestExplorerWalkthrough2")  
  
 Neste ponto, você criou um teste e um stub que você irá modificar para que o teste é aprovado.  
  
#### Após cada alteração, fazer todos os testes passarem  
  
1.  Em `MyMath\Rooter.cs`, melhorar o código de `SquareRoot`:  
  
    ```c#  
    public double SquareRoot(double input)  
     {  
       return input / 2;  
     }  
    ```  
  
2.  No Gerenciador de Testes, escolha **Executar Todos**.  
  
     Compila o código e o teste é executado.  
  
     O teste é aprovado.  
  
     ![Unidade Test Explorer mostrando um teste de passagem.](../test/media/unittestexplorerwalkthrough3.png "UnitTestExplorerWalkthrough3")  
  
#### Adicionar testes para estender o intervalo de entradas  
  
1.  Para aumentar sua confiança que seu código funciona em todos os casos, adicione os testes que tente uma variedade maior de valores de entrada.  
  
    > [!TIP]
    >  Evite alterar testes existentes que passaram. Em vez disso, adicione novos testes. Altere os testes existentes somente quando os requisitos de usuário forem alterados. Essa política ajuda a garantir que você não perde a funcionalidade existente enquanto você trabalha para estender o código.  
  
     Na classe de teste, adicione o seguinte teste, que tenta um intervalo de valores de entrada:  
  
    ```c#  
    [TestMethod]  
    public void RooterValueRange()  
    {  
      // Create an instance to test:  
      Rooter rooter = new Rooter();  
      // Try a range of values:  
      for (double expectedResult = 1e-8;  
          expectedResult < 1e+8;  
          expectedResult = expectedResult * 3.2)  
      {  
        RooterOneValue(rooter, expectedResult);  
      }  
    }  
  
    private void RooterOneValue(Rooter rooter, double expectedResult)  
    {  
      double input = expectedResult * expectedResult;  
      double actualResult = rooter.SquareRoot(input);  
      Assert.AreEqual(expectedResult, actualResult,  
          delta: expectedResult / 1000);  
    }  
    ```  
  
2.  No Gerenciador de Testes, escolha **Executar Todos**.  
  
     O novo teste falha, embora ainda passa o primeiro teste.  
  
     Para localizar o ponto de falha, selecione o teste com falha e, em seguida, na parte inferior do Gerenciador de testes, selecione o item superior do **rastreamento de pilha**.  
  
3.  Inspecione o método em teste para ver o que pode estar errado. No `MyMath.Rooter` da classe, reescrever o código:  
  
    ```  
    public double SquareRoot(double input)  
    {  
      double result = input;  
      double previousResult = -input;  
      while (Math.Abs(previousResult - result) > result / 1000)  
      {  
        previousResult = result;  
        result = result - (result * result - input) / (2 * result);  
      }  
      return result;  
    }  
    ```  
  
4.  No Gerenciador de Testes, escolha **Executar Todos**.  
  
     Ambos os testes agora passarem.  
  
#### Adicionar testes para casos excepcionais  
  
1.  Adicione um teste para entradas negativos:  
  
    ```c#  
    [TestMethod]  
     public void RooterTestNegativeInputx()  
     {  
         Rooter rooter = new Rooter();  
         try  
         {  
             rooter.SquareRoot(-10);  
         }  
         catch (ArgumentOutOfRangeException e)  
         {  
             return;  
         }  
         Assert.Fail();  
     }  
    ```  
  
2.  No Gerenciador de Testes, escolha **Executar Todos**.  
  
     O método sob teste loops e deve ser cancelado manualmente.  
  
3.  Escolha **Cancelar**.  
  
     O teste para após 10 segundos.  
  
4.  Corrigi o código do método:  
  
    ```c#  
  
    public double SquareRoot(double input)  
    {  
      if (input <= 0.0)   
      {  
        throw new ArgumentOutOfRangeException();  
      }   
    ...  
    ```  
  
5.  No Gerenciador de Testes, escolha **Executar Todos**.  
  
     Todos os testes passarem.  
  
#### Refatorar sem alterar os testes  
  
1.  Simplificar o código, mas não altera os testes.  
  
    > [!TIP]
    >  Um *refatoração* é uma alteração que é destinada para tornar o código funcionar melhor ou para tornar o código mais fácil de entender. Ele não deve alterar o comportamento do código e, portanto, os testes não são alterados.  
    >   
    >  É recomendável que você execute etapas refatoração separadamente das etapas que estendem a funcionalidade. Manter os testes inalterados proporciona confiança que você não acidentalmente introduziu bugs durante a refatoração.  
  
    ```c#  
    public class Rooter  
    {  
      public double SquareRoot(double input)  
      {  
        if (input <= 0.0)   
        {  
          throw new ArgumentOutOfRangeException();  
        }  
        double result = input;  
        double previousResult = -input;  
        while (Math.Abs(previousResult - result) > result / 1000)  
        {  
          previousResult = result;  
          result = (result + input / result) / 2;  
          //was: result = result - (result * result - input) / (2*result);  
        }  
        return result;  
      }  
    }  
    ```  
  
2.  Escolha **Executar todos**.  
  
     Todos os testes ainda passam.  
  
     ![Unidade Test Explorer mostrando 3 testes que passaram.](../test/media/unittestexplorerwalkthrough4.png "UnitTestExplorerWalkthrough4")