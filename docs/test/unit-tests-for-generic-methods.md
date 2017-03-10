---
title: "Testes de unidade para m&#233;todos gen&#233;ricos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Genéricos, e testes de unidade"
  - "testes de unidade, e genéricos"
ms.assetid: ffc89814-a7df-44fc-aef5-dd3dfeb28a9b
caps.latest.revision: 47
caps.handback.revision: 47
ms.author: "mlearned"
manager: "douge"
---
# Testes de unidade para m&#233;todos gen&#233;ricos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode gerar testes de unidade para métodos genéricos exatamente como faria para outros métodos, como descrito em [How to: Create and Run a Unit Test](http://msdn.microsoft.com/pt-br/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48).  As seções a seguir fornecem informações e exemplos de criação de testes de unidade para métodos genéricos.  
  
## Restrições de tipo e argumentos de tipo  
 Quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera um teste de unidade para uma classe genérica, como `MyList<T>`, ela gera dois métodos: um auxiliar genérico e um método de teste.  Se `MyList<T>` tem uma ou mais restrições de tipo, o argumento de tipo deve atender a todas as restrições de tipo.  Para ter certeza de que genérica de código sob teste funciona conforme o esperado para entradas de todos os permitidos, o método de teste chama o método auxiliar genérico com todas as restrições que você deseja testar.  
  
## Exemplos  
 Os exemplos a seguir ilustram os testes de unidade para genéricos:  
  
-   [Editando o código de teste gerado](#EditingGeneratedTestCode).  Este exemplo tem duas seções, código de teste gerado e o código de teste editada.  Ele mostra como editar o código de teste bruto que é gerado a partir de um método genérico em um método de teste úteis.  
  
-   [Usando uma restrição de tipo](#TypeConstraintNotSatisfied).  Este exemplo mostra um teste de unidade para um método genérico que usa uma restrição de tipo.  Neste exemplo, a restrição de tipo não for atendida.  
  
###  <a name="EditingGeneratedTestCode"></a> Exemplo 1: Editar código de teste gerado  
 O código de teste nesta seção testa um método de código sob teste chamado `SizeOfLinkedList()`.  Esse método retorna um inteiro que especifica o número de nós na lista vinculada.  
  
 O primeiro exemplo de código, na seção de código de teste gerado, mostra o código de teste não\-editada como ele foi gerado pelo Visual Studio Enterprise.  O segundo exemplo, na seção de código de teste editada, mostra como você pode torná\-lo a testar o funcionamento do método SizeOfLinkedList para dois tipos de dados diferentes, `int` e `char`.  
  
 Este código ilustra dois métodos:  
  
-   um método auxiliar de teste, `SizeOfLinkedListTestHelper<T>()`.  Por padrão, um método auxiliar de teste tem "TestHelper" em seu nome.  
  
-   um método de teste, `SizeOfLinkedListTest()`.  Cada método de teste é marcado com o atributo TestMethod.  
  
#### Código de teste gerado  
 O código de teste a seguir foi gerado a partir de `SizeOfLinkedList()` método.  Como esse é o teste gerado não\-editado, ele deve ser modificado para testar corretamente o método SizeOfLinkedList.  
  
```  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T); // TODO: Initialize to an appropriate value  
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value  
    int expected = 0; // TODO: Initialize to an appropriate value  
    int actual;  
    actual = target.SizeOfLinkedList();  
    Assert.AreEqual(expected, actual);  
    Assert.Inconclusive("Verify the correctness of this test method.");  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()  
{  
   SizeOfLinkedListTestHelper<GenericParameterHelper>();  
}  
```  
  
 No código anterior, o parâmetro de tipo genérico é `GenericParameterHelper`.  Enquanto você pode editá\-lo para fornecer tipos de dados específicos, como mostrado no exemplo a seguir, você pode executar o teste sem editar essa instrução.  
  
#### Edita o código de teste  
 No código a seguir, o método de teste e o método auxiliar de teste foram editadas para torná\-las com êxito o método de teste de código sob teste `SizeOfLinkedList()`.  
  
##### Testar o método auxiliar  
 O método auxiliar de teste executa as etapas a seguintes, que correspondem às linhas no código de rotulado como etapas de 1 a 5.  
  
1.  Crie uma lista vinculada genérica.  
  
2.  Acrescente quatro nós à lista vinculada.  O tipo de dados do conteúdo de nós é desconhecido.  
  
3.  Atribuir o tamanho esperado da lista vinculada à variável `expected`.  
  
4.  Calcular o tamanho real da lista vinculada e atribuí\-la à variável `actual`.  
  
5.  Comparar `actual` com `expected` em uma instrução Assert.  Se o valor real não é igual ao esperado, o teste falhar.  
  
##### Método de Teste  
 O método de teste é compilado para o código que é chamado quando você executar o teste chamado SizeOfLinkedListTest.  Ele executa as etapas a seguintes, que correspondem às linhas no código de rotulado etapas 6 e 7.  
  
1.  Especifique `<int>` quando você chama o método auxiliar de teste, para verificar se o teste funciona para `integer` variáveis.  
  
2.  Especifique `<char>` quando você chama o método auxiliar de teste, para verificar se o teste funciona para `char` variáveis.  
  
```  
  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T);   
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1  
    for (int i = 0; i < 4; i++) // step 2  
    {  
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);  
        target.Append(newNode);  
    }  
    int expected = 5; // step 3  
    int actual;  
    actual = target.SizeOfLinkedList(); // step 4  
    Assert.AreEqual(expected, actual); // step 5  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()   
{  
    SizeOfLinkedListTestHelper<int>();  // step 6  
    SizeOfLinkedListTestHelper<char>(); // step 7  
}  
```  
  
> [!NOTE]
>  Cada vez que o teste SizeOfLinkedListTest é executado, seu TestHelper método é chamado duas vezes.  A instrução assert deve ser avaliadas como true sempre para o teste seja aprovado.  Se o teste falhar, talvez não seja claro se a chamada especificada `<int>` ou a chamada especificado `<char>` causou a falha.  Para encontrar a resposta, você pode examinar a pilha de chamadas, ou você pode definir pontos de interrupção em seu método de teste e, em seguida, depurar durante a execução do teste.  Para obter mais informações, consulte [Como depurar durante a execução de um teste em uma solução do ASP.NET](../Topic/How%20to:%20Debug%20while%20Running%20a%20Test%20in%20an%20ASP.NET%20Solution.md).  
  
###  <a name="TypeConstraintNotSatisfied"></a> Exemplo 2: Usando uma restrição de tipo  
 Este exemplo mostra um teste de unidade para um método genérico que usa uma restrição de tipo que não seja atendida.  A primeira seção mostra o código do projeto de código sob teste.  A restrição de tipo é realçada.  
  
 A segunda seção mostra o código do projeto de teste.  
  
#### Projeto de código sob teste  
  
```  
using System;  
using System.Linq;  
using System.Collections.Generic;  
using System.Text;  
  
namespace ClassLibrary2  
{  
    public class Employee  
    {  
        public Employee(string s, int i)  
        {  
        }  
    }  
  
    public class GenericList<T> where T : Employee  
    {  
        private class Node  
        {  
            private T data;  
            public T Data  
            {  
                get { return data; }  
                set { data = value; }  
            }  
        }  
    }  
}  
```  
  
#### Projeto de Teste  
 Assim como acontece com todos os testes de unidade, você deve adicionar instruções de declaração não inconclusivo para teste de unidade para torná\-lo a retornar resultados úteis.  Você não adicioná\-los para o método marcado com o atributo TestMethod, mas para o método "TestHelper", que é chamado para este teste `DataTestHelper<T>()`.  
  
 Neste exemplo, parâmetro de tipo genérico `T` tem a restrição `where T : Employee`.  Essa restrição não for atendida no método de teste.  Portanto, o `DataTest()` método contém uma instrução Assert que alerta sobre a necessidade de fornecer a restrição de tipo que foi colocada em `T`.  A mensagem dessa instrução Assert diz o seguinte: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`  
  
 Em outras palavras, quando você chama o `DataTestHelper<T>()` método a partir do método de teste, `DataTest()`, você deve passar um parâmetro do tipo `Employee` ou uma classe derivada de `Employee`.  
  
 `using ClassLibrary2;`  
  
 `using Microsoft.VisualStudio.TestTools.UnitTesting;`  
  
 `namespace TestProject1`  
  
```  
{  
    [TestClass()]  
    public class GenericList_NodeTest  
    {  
  
        public void DataTestHelper<T>()  
            where T : Employee  
        {  
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value  
            T expected = default(T); // TODO: Initialize to an appropriate value  
            T actual;  
            target.Data = expected;  
            actual = target.Data;  
            Assert.AreEqual(expected, actual);  
            Assert.Inconclusive("Verify the correctness of this test method.");  
        }  
  
        [TestMethod()]  
        public void DataTest()  
        {  
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +  
            "Please call DataTestHelper<T>() with appropriate type parameters.");  
        }  
    }  
}  
```  
  
## Consulte também  
 [Anatomy of a Unit Test](http://msdn.microsoft.com/pt-br/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Teste de unidade de código](../test/unit-test-your-code.md)