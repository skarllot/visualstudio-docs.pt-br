---
title: "Funções (JavaScript) | Microsoft Docs"
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
- intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: fd5626af6417b5f0010545874bd15c86b30a303a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="functions-javascript"></a>Funções (JavaScript)
As funções [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] executam ações. Elas também podem retornar valores. Às vezes, eles são resultados de cálculos ou comparações. Funções também são chamadas de "métodos globais".  
  
 Elas combinam diversas operações em um nome. Isso permite simplificar seu código. Você pode escrever um conjunto de instruções, nomeá-lo e executar todo o conjunto chamando-o e transmitindo a ele todas as informações necessárias.  
  
 Você transmite informações a uma função colocando as informações entre parênteses após o nome da função. Trechos de informações que são transmitidos a uma função são chamados de argumentos ou parâmetros. Algumas funções não usam nenhum argumento, enquanto outras usam um ou mais argumentos. Em algumas funções, o número de argumentos depende de como você está usando a função.  
  
 O [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dá suporte a dois tipos de funções: aquelas que são internas à linguagem e as que são criadas por você.  
  
## <a name="built-in-functions"></a>Funções internas  
 A linguagem [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] inclui várias funções internas. Algumas delas permitem que você processe expressões e caracteres especiais, enquanto outras convertem cadeias de caracteres em valores numéricos.  
  
 Consulte [Métodos JavaScript](../javascript/reference/javascript-methods.md) para obter informações sobre essas funções internas.  
  
## <a name="creating-your-own-functions"></a>Criando suas próprias funções  
 Você pode criar suas próprias funções e usá-las quando for necessário. Uma definição de função consiste em uma instrução de função e um bloco de instruções [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 A função **checkTriplet** no exemplo a seguir usa os comprimentos dos lados de um triângulo como argumentos. Ela calcula por meio deles se o triângulo é um triângulo retângulo verificando se os três números constituem um trio de Pitágoras (o quadrado do comprimento da hipotenusa de um triângulo retângulo é igual à soma dos quadrados dos comprimentos dos outros dois lados). A função checkTriplet chama uma das duas outras funções para fazer o teste.  
  
 Observe o uso de um número muito pequeno ("épsilon") como variável de teste na versão de ponto flutuante do teste. Devido a incertezas e erros de arredondamento em cálculos de ponto flutuante, não é prático testar diretamente se os três números constituem um trio de Pitágoras, a menos que se saiba que os três valores em questão são inteiros. Como um teste direto é mais preciso, o código neste exemplo determina se ele é apropriado e, se for, o utiliza.  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>Funções de seta  
 A sintaxe de função de seta, `=>`, fornece um método abreviado de especificar uma função anônima. Esta é a sintaxe de função de seta.  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 Os valores à esquerda da seta, que podem ser delimitados por parênteses, especificam os argumentos transmitidos para a função. Um único argumento para a função não requer parênteses. Se nenhum argumento for passado, são necessários parênteses. A definição da função à direita da seta pode ser uma expressão, como `v + 1`, ou um bloco de instruções entre chaves ({}).  
  
> [!IMPORTANT]
>  A sintaxe de função de seta tem suporte apenas no [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Não é possível usar o operador `new` com uma função de seta.  
  
 Os exemplos de código a seguir mostram o uso da função de seta com expressões como as definições de função. No primeiro exemplo, v é transmitido como o argumento para a expressão. No segundo exemplo, v e i são transmitidos como argumentos para a expressão.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 O exemplo de código mostra o uso da função de seta com um bloco de instruções.  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 Diferente das funções padrão, as funções de Seta compartilham o mesmo objeto lexical `this` que o código ao redor, o que pode ser usado para eliminar a necessidade de soluções alternativas, como `var self = this;`.  
  
 O exemplo a seguir mostra que o valor do objeto `this` dentro da função de seta é o mesmo que o código ao redor (ainda se refere à variável `bob` variável).  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 As funções de seta também compartilham o mesmo objeto lexical `arguments` que o código ao redor (como o objeto `this`).  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>Parâmetros padrão  
 Você pode especificar um valor padrão para um parâmetro em uma função atribuindo a ele um valor inicial. O valor padrão pode ser um valor constante ou uma expressão.  
  
> [!IMPORTANT]
>  Parâmetros padrão têm suporte apenas no [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)].  
  
 No exemplo a seguir, o valor padrão de y é 10 e o valor padrão de z é 20. A função usará 10 como valor de y, a menos que o chamador transmita um valor distinto (ou indefinido) como segundo argumento. A função usará 20 como valor de z, a menos que o chamador transmita um valor distinto (ou indefinido) como terceiro argumento.  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>Parâmetros Rest  
 Parâmetros Rest, especificados pelo operador de espalhamento (), permitem que você transforme argumentos consecutivos em uma chamada de função para uma matriz.  
  
 Parâmetros Rest eliminam a necessidade do objeto `arguments`. Parâmetros Rest diferem do objeto `arguments` de diversas maneiras, como:  
  
-   Um parâmetro rest é uma instância de matriz e, portanto, dá suporte a operações que podem ser executadas em uma matriz.  
  
-   Um parâmetro rest inclui apenas os argumentos consecutivos que não são transmitidos como argumentos separados (nomeados) (por outro lado, o objeto `arguments` contém todos os argumentos transmitidos para a função).  
  
> [!IMPORTANT]
>  Parâmetros Rest e o operador de espalhamento têm suporte apenas no [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 No exemplo de código a seguir, true e "hello" são transmitidos como valores de matriz e armazenados no parâmetro y. O parâmetro rest deve ser o último parâmetro da função.  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 Para ver usos adicionais do operador de espalhamento, consulte [Operador de Espalhamento](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linguagem JavaScript](../javascript/javascript-language-reference.md)
