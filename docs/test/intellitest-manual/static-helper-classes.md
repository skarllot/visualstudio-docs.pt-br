---
title: "Classes auxiliares estáticas | Ferramenta de teste do desenvolvedor do Microsoft IntelliTest | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.assetid: 1EE26913-E498-492E-BB90-BB0D6E8A097C
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
ms.openlocfilehash: f34de68d44b8a7e37647c460cb4402e1c19ad088
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="static-helper-classes"></a>Classes auxiliares estáticas

O IntelliTest fornece um conjunto de classes auxiliares estáticas que pode ser usado ao criar [testes de unidade parametrizados](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): usado para definir suposições sobre entradas e é útil para filtrar entradas indesejáveis
* [PexAssert](#pexassert): uma classe de declaração simples para usar se a estrutura de teste não fornecer uma
* [PexChoose](#pexchoose): um fluxo de entradas de teste adicionais que gerencia o IntelliTest
* [PexObserve](#pexobserve): registra valores concretos e, opcionalmente, os valida no código gerado

Algumas classes permitem que você interaja com o mecanismo de raciocínio do IntelliTest em um nível inferior:

* [PexSymbolicValue](#pexsymbolicvalue): utilitários para inspecionar ou modificar restrições simbólicas em variáveis

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Uma classe estática usada para expressar suposições, tais como [pré-condições](test-generation.md#precondition), nos [testes de unidade parametrizados](test-generation.md#parameterized-unit-testing).
Os métodos dessa classe podem ser usados para filtrar as entradas de teste indesejáveis.

Se a condição assumida não valer para alguma entrada de teste, uma **PexAssumeFailedException** é lançada. Isso fará com que o teste seja ignorado silenciosamente.

**Exemplo**

O teste parametrizado a seguir não considerará **j=0**:

```
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Comentários**

O código acima é quase equivalente a:

```
     if (j==0)
          return;
```

exceto que um **PexAssume** com fala resulta não resulta em nenhum caso de teste. No caso de uma instrução **if**, o IntelliTest gera um caso de teste separado para abranger o branch **then** da instrução **if**.

O **PexAssume** também contém classes aninhadas especializadas para suposições na cadeia de caracteres, matrizes e coleções.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Uma classe estática usada para expressar declarações, tais como [pós-condições](test-generation.md#postcondition), nos [testes de unidade parametrizados](test-generation.md#parameterized-unit-testing).

Se a condição declarada não valer para algumas entradas de teste, um **PexAssertFailedException** é gerado, o que faz com que o teste falhe.

**Exemplo**

O exemplo a seguir declara que o valor absoluto de um inteiro é positivo:

```
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Uma classe estática que fornece valores de entrada auxiliares para um teste, o que pode ser usado para implementar [Simulações Parametrizadas](input-generation.md#parameterized-mocks).

A classe **PexChoose** não ajuda a determinar se um teste passa ou falha para valores de entrada específicos. O **PexChoose** simplesmente fornece valores de entrada, que também são conhecidos como *opções*. Ainda depende do usuário restringir os valores de entrada e escrever declarações que definem quando um teste é aprovado ou falha.

**Modos de operação**

A classe **PexChoose** pode operar em dois modos:

* Enquanto o IntelliTest está executando uma análise simbólica do teste e do código testado durante a [geração de entrada](input-generation.md), o seletor retorna valores arbitrários e o IntelliTest controla como cada valor é usado no teste e no código testado. O IntelliTest gerará valores relevantes para disparar caminhos de execução diferentes no teste e no código testado.

* O código gerado para casos de teste específicos define o provedor de escolha de uma maneira de forma que a nova execução de tal caso de teste fará escolhas específicas para disparar um caminho de execução específico.

**Uso**

* Basta chamar **PexChoose.Value** para gerar um novo valor:

```
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Uma classe estática para registrar valores nomeados.

Quando o IntelliTest explora o código, o **PexObserve** é usado para registrar os valores calculados usando suas representações de cadeia de caracteres formatada. Os valores são associados a nomes exclusivos.

```
PexObserve.Value<string>("result", result);
```

**Exemplo**

```
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}


// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a); 
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Uma classe estática usada para ignorar restrições em parâmetros e imprimir as informações simbólicas associadas aos valores.

**Uso**

Normalmente, o IntelliTest tenta abranger todos os caminhos de execução do código durante a execução. No entanto, especialmente ao computar condições de declaração e suposição, ele não deve explorar todos os casos possíveis.

**Exemplo**

Este exemplo mostra a implementação do método **PexAssume.Arrays.ElementsAreNotNull**. No método, você ignora as restrições no tamanho do valor da matriz para evitar que o IntelliTest tente gerar diferentes tamanhos de matriz. As restrições são ignoradas somente aqui. Se o código testado tiver um comportamento diferente de comprimentos de matriz diferente, o IntelliTest não poderá gerar matrizes de tamanhos diferentes das restrições no código testado.

```
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Recebeu comentários?

Poste suas ideias e solicitações de recursos no  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

