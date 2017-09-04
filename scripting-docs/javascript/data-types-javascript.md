---
title: Tipos de dados (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="data-types-javascript"></a>Tipos de dados (JavaScript)
Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], há três tipos de dados primários, dois tipos de dados de composição e dois tipos de dados especiais.  
  
## <a name="primary-data-types"></a>Tipos de Dados Primários  
 Os tipos de dados primários (primitivos) são:  
  
-   Cadeia de caracteres  
  
-   Número  
  
-   Boolean  
  
## <a name="composite-data-types"></a>Tipos de dados compostos  
 Os tipos de dados de composição (de referência) são:  
  
-   Objeto  
  
-   Matriz  
  
## <a name="special-data-types"></a>Tipos de Dados Especiais  
 Os tipos de dados especiais são:  
  
-   Nulo  
  
-   Indefinido  
  
## <a name="string-data-type"></a>Tipo de dados da cadeia de caracteres  
 Um valor de cadeia de caracteres é uma cadeia de zero ou mais caracteres Unicode (letras, dígitos e marcas de pontuação). Use o tipo de dados String para representar texto em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Você pode incluir literais de cadeia de caracteres em seus scripts, colocando-os entre aspas simples ou duplas. Aspas duplas podem estar contidas em cadeias de caracteres entre aspas simples, enquanto aspas simples podem estar contidas em cadeias de caracteres entre aspas duplas. Veja a seguir alguns exemplos de cadeias de caracteres:  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Observe que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] não tem um tipo para representar um único caractere. Para representar um único caractere em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], você cria uma cadeia de caracteres que consiste em apenas um caractere. Uma cadeia de caracteres que contém zero caracteres ("") é uma cadeia de caracteres vazia (tamanho zero).  
  
 O [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fornece sequências de escape que você pode incluir em cadeias de caracteres para criar caracteres que não podem ser digitados diretamente. Por exemplo, `\t` especifica um caractere de tabulação. Para obter mais informações, consulte [Caracteres especiais](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Tipo de Dados de Número  
 Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], não há nenhuma distinção entre valores inteiros e de ponto flutuante; um número [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] pode ser qualquer um deles (internamente, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] representa todos os números como valores de ponto flutuante).  
  
### <a name="integer-values"></a>Valores Inteiros  
 Valores inteiros podem ser números inteiros positivos, números inteiros negativos e 0. Eles podem ser representados na base 10 (decimal), na base 16 (hexadecimal) e na base 8 (octal). A maioria dos números em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] são gravados em base decimal.  
  
 Você denota inteiros hexadecimais ("hex") prefixando-os com um "0x" à esquerda (zero e x&#124;X). Eles podem conter apenas dígitos de 0 a 9 e letras de A a F (maiúsculas ou minúsculas). As letras de A a F são usadas para representar, como dígitos únicos, 10 a 15 na base 10. Ou seja, 0xF é equivalente a 15 e 0x10 é equivalente a 16.  
  
 Você denota inteiros octais prefixando-os com um "0" à esquerda (zero). Eles podem conter apenas dígitos de 0 a 7. Um número que tem um "0" à esquerda e contém os dígitos "8" e/ou "9" é interpretado como um número decimal.  
  
 Números hexadecimais e octais podem ser negativos, mas eles não podem ter uma parte decimal nem ser gravados em notação científica (exponencial).  
  
> [!NOTE]
>  Começando em [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], a [função parseInt](../javascript/reference/parseint-function-javascript.md) não trata uma cadeia de caracteres que tem um prefixo de "0" como octal. Quando você não estiver usando a função `parseInt`, no entanto, cadeias de caracteres com um prefixo "0" ainda poderão ser interpretadas como octais.  
  
### <a name="floating-point-values"></a>Valores de Ponto Flutuante  
 Valores de ponto flutuante podem ser números inteiros com uma parte decimal. Além disso, eles podem ser expressos em notação científica. Ou seja, um "e" maiúsculo ou minúsculo é usado para representar "dez à potência de". [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] representa números usando o padrão de ponto flutuante IEEE 754 de oito bytes para representação numérica. Isso significa que você pode escrever números tão grandes quanto 1.79769x10<sup>308</sup> e tão pequenos quanto 5x10<sup>-324</sup>. Um número que contém um ponto decimal e que tem um único "0" antes do ponto decimal é interpretado como um número decimal de ponto flutuante.  
  
 Observe que um número que começa com "0x" ou "00" e contém um ponto decimal gerará um erro. Aqui estão alguns exemplos de números [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Número|Descrição|Decimal equivalente|  
|------------|-----------------|------------------------|  
|.0001, 0.0001, 1e-4, 1.0e-4|Quatro números de ponto flutuante equivalentes.|0.0001|  
|3.45e2|Um número de ponto flutuante.|345|  
|45|Um inteiro.|45|  
|0378|Um inteiro. Embora isso pareça um número octal (começa com um zero), 8 não é um dígito octal válido, então o número é tratado como um decimal.|378|  
|0377|Um inteiro octal. Observe que embora ele pareça ser apenas uma unidade menor que o número acima, o valor real é bastante diferente.|255|  
|0.0001|Número de ponto flutuante. Embora isso comece com um zero, ele não é um número octal porque tem um ponto decimal.|0.0001|  
|00.0001|Isso é um erro. Os dois zeros à esquerda marcam o número como um octal, mas octais não são permitidos para um componente decimal.|N/D (erro do compilador)|  
|0Xff|Um inteiro hexadecimal.|255|  
|0x37CF|Um inteiro hexadecimal.|14287|  
|0x3e7|Um inteiro hexadecimal. Observe que o 'e' não é tratado como exponenciação.|999|  
|0x3.45e2|Isso é um erro. Números hexadecimais não podem ter partes decimais.|N/D (erro do compilador)|  
  
 Além disso, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contém números com valores especiais. Elas são:  
  
-   NaN (não é um número). Isso é usado quando uma operação matemática é executada em dados inadequados, tais como cadeias de caracteres ou o valor indefinido  
  
-   Infinito positivo. Isso é usado quando um número positivo é grande demais para representar em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Infinito negativo. Isso é usado quando um número negativo é grande demais para representar em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   0 positivo e negativo. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] faz distinção entre zero positivo e negativo.  
  
## <a name="boolean-data-type"></a>Tipo de dados booliano  
 Enquanto os tipos de dados String e Number podem ter um número praticamente ilimitado de valores diferentes, o tipo de dados Boolean só pode ter dois. Eles são os literais `true` e `false`. Um valor booliano é um valor de verdade: Especifica se a condição é verdadeira ou não.  
  
 As comparações feitas em seus scripts sempre têm um resultado booliano. Considere a seguinte linha de código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
y = (x == 2000);  
```  
  
 Aqui, o valor da variável `x` é comparado com o número 2000. Se for, o resultado da comparação é o valor booliano **true**, que é atribuído à variável `y`. Se `x` não é igual a 2000, o resultado da comparação é o valor booliano `false`.  
  
 Valores boolianos são especialmente úteis em estruturas de controle. O código a seguir combina uma comparação que cria um valor booliano diretamente com uma instrução que a utiliza. Considere o exemplo de código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] a seguir.  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 A instrução `if/else` em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] executará uma ação se um valor booliano for `true` (`z = z + 1`) e outra ação se o valor booliano for `false` (`x = x + 1`).  
  
 Você pode usar qualquer expressão como uma expressão de comparação. Qualquer expressão avaliada como 0, null, indefinido ou uma cadeia de caracteres vazia é interpretada como `false`. Uma expressão avaliada como qualquer outro valor será interpretada como `true`. Por exemplo, você poderia usar uma expressão como:  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Observe que a linha acima não verifica se `x` é igual a `y + z`, já que apenas um único sinal de igual (o operador de atribuição) é usado. Em vez disso, o código acima atribui o valor de `y + z` à variável `x` e, em seguida, verifica se o resultado da expressão inteira (o valor de `x`) é igual a zero. Para verificar se `x` é igual a `y + z`, você precisa usar o código a seguir.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Para obter mais informações sobre as comparações, consulte [Controlar o fluxo do programa](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>O Tipo de Dados nulo  
 O tipo de dados `null` tem apenas um valor em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: nulo. A palavra-chave `null` não pode ser usada como o nome de uma função ou variável.  
  
 Uma variável que contém `null` não contém nenhum número, cadeia de caracteres, booliano, matriz ou objeto válido. Você pode apagar o conteúdo de uma variável (sem excluir a variável) atribuindo a ele o valor `null`.  
  
 Observe que em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` não é o mesmo que 0 (ao contrário do que ocorre em C e C++). Observe também que o operador `typeof` em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] relata valores `null` como sendo do tipo `Object` e não do tipo `null`. Esse comportamento é potencialmente confuso para compatibilidade com versões anteriores.  
  
## <a name="the-undefined-data-type"></a>O Tipo de Dados indefinido  
 O valor `undefined` é retornado quando você usa uma propriedade de objeto que não existe ou então uma variável que foi declarada mas nunca teve um valor atribuído a ela.  
  
 Você pode verificar se uma variável existe, comparando-a a `undefined`, embora você possa verificar se o tipo dela é `undefined` comparando o tipo da variável à cadeia de caracteres "undefined". O exemplo a seguir mostra como descobrir se a variável `x` foi declarada:  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 Você também pode comparar o valor indefinido a `null`. Essa comparação é `true` se a propriedade `someObject.prop` é `null` ou se a propriedade `someObject.prop` não existe.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Para saber se uma propriedade de objeto existe, você pode usar o operador **in**:  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>Consulte também  
 [Objetos e matrizes](../javascript/objects-and-arrays-javascript.md)   
 [Operador TypeOf](../javascript/reference/typeof-operator-decrementjavascript.md)
