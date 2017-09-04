---
title: Iteradores e geradores (JavaScript) | Microsoft Docs
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
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 85c27969609a38b87b15c727e9c8aef89ee77032
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="iterators-and-generators-javascript"></a>Iteradores e geradores (JavaScript)
Um iterador é um objeto usado para percorrer um objeto de contêiner, como uma lista. No JavaScript, um objeto iterador não é um objeto interno distinto, e sim um objeto que implementa um método `next` para acessar o próximo item no objeto de contêiner.  
  
 Em [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], é possível criar seus próprios iteradores personalizados. No entanto, geralmente é mais fácil usar geradores, que simplificam muito a criação de iteradores. Geradores são um tipo de função que funciona como uma fábrica de iteradores. Para criar um iterador personalizado usando uma função de gerador, consulte [Geradores](#Generators).  
  
> [!CAUTION]
>  Geradores têm suporte no [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="iterators"></a>Iteradores  
 A implementação de um iterador de JavaScript envolve dois ou três objetos que estão em conformidade com interfaces específicas:  
  
-   Interface que pode ser iterada  
  
-   Interface de iterador  
  
-   Interface IteratorResult  
  
 Usando essas interfaces, você pode criar iteradores personalizados. Isso permite que você percorra um objeto que pode ser iterado usando a instrução `for…of`.  
  
### <a name="iterable-interface"></a>Interface que pode ser iterada  
 A interface que pode ser iterada é a interface necessária para um objeto que pode ser iterado (um objeto para o qual um iterador pode ser obtido). Por exemplo, `C` em `for (let e of C)` deve implementar a interface que pode ser iterada.  
  
 Um objeto que pode ser iterado deve fornecer o método Symbol.iterator, que retorna um iterador.  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 Essa propriedade deve ser uma função que não aceita argumentos e retorna um objeto (`iterObject`) que está em conformidade com a interface `Iterator`.  
  
 Muitos tipos internos, inclusive matrizes, são agora pode ser iterados. O loop `for…of` consome um objeto que pode ser iterado. (No entanto, nem todos os elementos internos que podem ser iterados são iteradores. Por exemplo, um objeto de Matriz não é um iterador em si, mas pode ser iterado, enquanto um ArrayIterator também pode ser iterado.)  
  
### <a name="iterator-interface"></a>Interface de iterador  
 O objeto retornado pelo método Symbol.iterator deve implementar o método `next`. O método `next` tem a seguinte sintaxe.  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 O método `next` é uma função que retorna um valor. A função retorna um objeto (`iterResultObj`) que está em conformidade com a interface `IteratorResult`. Se uma chamada anterior para o método `next` de um iterador retornar um objeto `IteratorResult` cuja propriedade `done` for verdadeira, a iteração é encerrada e o método `next` não é chamado novamente.  
  
 Iteradores também podem incluir um método `return` para garantir que o iterador seja descartado corretamente quando o script for concluído com ele.  
  
### <a name="iteratorresult-interface"></a>Interface IteratorResult  
 Uma interface IteratorResult é a interface necessária para o resultado do método `next` em um iterador. O objeto retornado por `next` deve fornecer uma propriedade `done` e `value`.  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 A propriedade `done` retorna o status de uma chamada do método `next` do iterador, verdadeira ou falsa. Se o final do iterador foi atingido, `done` retorna verdadeiro. Se o final não for atingido, `done` retorna falso e um valor fica disponível. Se a propriedade `done` (seja própria ou uma propriedade herdada) não existir, o resultado de `done` será tratado como falso.  
  
 Se `done` for falso, a propriedade `value` retorna o valor do elemento de iteração atual. Se `done` for verdadeiro, este é o valor retornado do iterador, se for fornecido um valor retornado. Se o iterador não tiver um valor retornado, `value` é indefinido. Nesse caso, a propriedade `value` pode estar ausente do objeto em conformidade se ele não herdar uma propriedade de valor explícito.  
  
<a name="Generators"></a>   
## <a name="generators"></a>Geradores  
 Para criar e usar iteradores personalizados com facilidade, crie uma função de gerador usando a sintaxe de função* junto com um ou mais expressões `yield`. A função de gerador retorna um iterador (ou seja, um gerador), o que permite que o corpo da função de gerador seja executado. A função é executada para a próxima instrução `yield` ou `return`.  
  
 Chame o método `next` do iterador para retornar o próximo valor da função do gerador.  
  
 O exemplo a seguir mostra um gerador que retorna um iterador para um objeto de cadeia de caracteres.  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 Em um gerador, a expressão do operando de rendimento encerra a chamada para `next` e retorna um objeto `IteratorResult` com duas propriedades, `done` (`done=false`) e `value` (`value=operand`). `operand` é opcional e se ficar ausentes, seu valor será indefinido.  
  
 Em um gerador, uma instrução `return` finaliza o gerador retornando um `IteratorResult` com `done=true`, juntamente com o resultado de operando opcional para a propriedade de valor.  
  
 Você também pode usar uma expressão `yield*` no lugar de `yield` para delegar para outro gerador ou outro objeto que pode ser iterado, como uma matriz ou cadeia de caracteres.  
  
 Se você acrescentar o código a seguir ao exemplo anterior, `yield*` delega para o gerador `stringIter`.  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 Você também pode criar geradores mais avançados passando um argumento para `next` e usando o argumento para modificar o estado do gerador. `next` torna-se o valor do resultado da expressão `yield` executada anteriormente. No exemplo a seguir, quando passa um valor de 100 para o método `next`, você redefine o valor do índice interno do gerador.  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 Outros geradores avançados podem chamar o método `throw` do gerador. O erro parece ser gerado no ponto em que o gerador é pausado (antes da próxima instrução `yield`).

