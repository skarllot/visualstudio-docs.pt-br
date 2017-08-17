---
title: Operadores (JavaScript) | Microsoft Docs
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
- JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="operators-javascript"></a>Operadores (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] tem uma gama completa de operadores, incluindo aritméticos, lógicos, bit a bit, de atribuição, bem como alguns operadores diversos. Para obter explicações e exemplos, consulte os tópicos sobre operadores específicos.  
  
## <a name="computational-operators"></a>Operadores Computacionais  
  
|Descrição|Símbolo|  
|-----------------|------------|  
|[Negação unária](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Incremento](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[Decremento](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Multiplicação](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[Divisão](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Módulo aritmético](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Adição](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Subtração](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Operadores Lógicos  
  
|Descrição|Símbolo|  
|-----------------|------------|  
|[NOT lógico](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Menor que](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Maior que](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Menor ou igual a](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Maior ou igual a](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Igualdade](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Desigualdade](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[AND lógico](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[OR lógico](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Condicional (ternário)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Vírgula](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Igualdade estrita](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Desigualdade estrita](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Operadores Bit a Bit  
  
|Descrição|Símbolo|  
|-----------------|------------|  
|[NOT bit a bit](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Bit a bit de deslocamento para a esquerda](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Bit a bit de deslocamento para a direita](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Deslocamento para a direita sem sinal](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[AND bit a bit](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[XOR bit a bit](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[OR bit a bit](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Operadores de atribuição  
  
|Descrição|Símbolo|  
|-----------------|------------|  
|[Atribuição](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Atribuição composta](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (assim como += e &=)|  
  
## <a name="miscellaneous-operators"></a>Operadores diversos  
  
|Descrição|Símbolo|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|excluir|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|em|  
  
## <a name="equality-and-strict-equality"></a>Igualdade e Igualdade Estrita  
 A diferença entre == (igualdade) e === (igualdade estrita) é que o operador de igualdade forçará valores de tipos diferentes antes de verificar a igualdade. Por exemplo, a comparação de cadeia de caracteres "1" com o número 1 resultará em true. O operador de igualdade estrita, por outro lado, não fará imposição de valores para tipos diferentes, portanto, a cadeia de caracteres "1" não será considerada igual ao número 1 ao compará-los.  
  
 Cadeias de caracteres, boolianos e números primitivos são comparados por valor. Se eles têm o mesmo valor, eles são iguais. Objetos (incluindo objetos de `Array`, `Function`, `String`, **número**, `Boolean`, **erro**, `Date` e `RegExp`) são comparados por referência. Mesmo se duas variáveis desses tipos têm o mesmo valor, eles são iguais somente caso se refiram a exatamente o mesmo objeto.  
  
 Por exemplo:  
  
```JavaScript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```
