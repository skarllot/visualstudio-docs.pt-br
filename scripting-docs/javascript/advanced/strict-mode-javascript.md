---
title: Modo Estrito (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="strict-mode-javascript"></a>Modo estrito (JavaScript)
Modo estrito é uma maneira de introduzir uma melhor verificação de erros em seu código. Quando você usa o modo estrito, você não pode, por exemplo, usar variáveis declaradas implicitamente, nem atribuir um valor a uma propriedade somente leitura ou tampouco adicionar uma propriedade a um objeto que não é extensível. As restrições estão listadas na seção [Restrições em código no modo estrito](../../javascript/advanced/strict-mode-javascript.md#rest), mais adiante neste tópico. Para obter informações adicionais sobre o modo estrito, consulte [Especificação da linguagem ECMAScript, 5ª edição](http://www.ecma-international.org/publications/standards/Ecma-262.htm).  
  
> [!WARNING]
>  O modo estrito não é compatível com as versões do Internet Explorer anteriores ao Internet Explorer 10.  
  
## <a name="declaring-strict-mode"></a>Declarando o modo estrito  
 Você pode declarar o modo estrito adicionando `"use strict";` no início de um arquivo, programa ou função. Esse tipo de declaração é conhecido como um *prólogo de diretivas*. O escopo de uma declaração de modo estrito depende do contexto dela. Se ela for declarada em um contexto global (fora do escopo de uma função), todo o código no programa está no modo estrito. Se ela for declarada em uma função, todo o código na função está no modo estrito. No exemplo a seguir, todo o código está no modo estrito e a declaração de variável fora da função causa o erro de sintaxe "Variável indefinida no modo estrito."  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 No exemplo a seguir, somente o código dentro de `testFunction` está no modo estrito. A declaração de variável fora da função não causa um erro de sintaxe, mas a declaração dentro da função sim.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Restrições em código no modo estrito  
 A tabela a seguir lista as restrições mais importantes que se aplicam no modo estrito.  
  
|||||  
|-|-|-|-|  
|**Elemento de linguagem**|**Restrição**|**Erro**|**Exemplo**|  
|Variável|Usar uma variável sem declará-la.|SCRIPT5042: variável não definida no modo estrito|`testvar = 4;`|  
|Propriedade somente leitura|Gravar em uma propriedade somente leitura.|SCRIPT5045: a atribuição a propriedades somente leitura não é permitida no modo estrito|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Propriedade não extensível|Adicionar uma propriedade a um objeto cujo atributo `extensible` é definido como `false`.|SCRIPT5046: não é possível criar a propriedade de um objeto não extensível|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Excluir uma variável, uma função ou um argumento.<br /><br /> Excluir uma propriedade cujo atributo `configurable` é definido como `false`.|SCRIPT1045: chamar delete em \<expressão> não é permitido no modo estrito|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Duplicar uma propriedade|Definir uma propriedade mais de uma vez em um literal de objeto.|SCRIPT1046: várias definições de uma propriedade que não é permitida no modo estrito|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Duplicar um nome de parâmetro|Usar um nome de parâmetro mais de uma vez em uma função.|SCRIPT1038: nomes de parâmetro formais duplicados não são permitidos no modo estrito|`function testFunc(param1, param1) {     return 1; };`|  
|Palavras-chave reservadas futuras|Usando uma palavra-chave reservada futura como um nome de função ou de variável.|SCRIPT1050: o uso de uma palavra reservada futura para um identificador é inválido. O nome do identificador é reservado no modo estrito.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Octais|Atribuir um valor octal de um literal numérico ou tentar usar um escape em um valor octal.|SCRIPT1039: os literais numéricos octais e caracteres de escape não são permitidos no modo estrito|`var testoctal = 010; var testescape = \010;`|  
|`this`|O valor de `this` não é convertido no objeto global quando esse valor é `null` ou `undefined`.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> No modo não restrito, o valor de `testvar` é o objeto global, mas no modo estrito o valor é `undefined`.|  
|`eval` como um identificador|A cadeia de caracteres "eval" não pode ser usada como um identificador (nome de variável ou função, o nome do parâmetro e assim por diante).||`var eval = 10;`|  
|Função declarada dentro de uma instrução ou um bloco|Você não pode declarar uma função dentro de uma instrução ou bloco.|SCRIPT1047: no modo estrito, declarações de função não podem ser aninhadas dentro de uma instrução ou bloco. Elas só podem aparecer no nível superior ou diretamente dentro de um corpo de função.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Variável declarada dentro de uma função `eval`|Se uma variável é declarada dentro de uma função `eval`, ela não pode ser usada fora da função.|SCRIPT1041: o uso inválido de 'eval' no modo estrito|`eval("var testvar = 10"); testvar = 15;`<br /><br /> A avaliação indireta é possível, mas você não pode usar uma variável declarada fora da função `eval`.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Este código causa um erro SCRIPT5009: 'testVar' é indefinido.|  
|`Arguments` como um identificador|A cadeia de caracteres "arguments" não pode ser usada como um identificador (nome de variável ou função, o nome do parâmetro e assim por diante).|SCRIPT1042: uso inválido de 'arguments' no modo estrito|`var arguments = 10;`|  
|`arguments` dentro de uma função|Você não pode alterar os valores dos membros do objeto `arguments` local.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> No modo não estrito, você pode alterar o valor do parâmetro `oneArg` alterando o valor de `arguments[0]`, de modo que o valor de ambos `oneArg` e `arguments[0]` é 20. No modo estrito, alterar o valor de `arguments[0]` não afeta o valor de `oneArg`, pois o objeto `arguments` é apenas uma cópia local.|  
|`arguments.callee`|Não permitido.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|Não permitido.|SCRIPT1037: instruções 'with' não são permitidas no modo estrito|`with (Math){     x = cos(3);     y = tan(7); }`|
