---
title: "Escrevendo código JavaScript | Microsoft Docs"
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
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="writing-javascript-code"></a>Escrevendo código JavaScript
Como muitas outras linguagens de programação, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] é organizado em instruções, comentários e blocos consistindo de conjuntos de instruções relacionados. Dentro de uma instrução você pode usar variáveis, cadeias de caracteres, números e expressões.  
  
## <a name="statements"></a>Instruções  
 Um programa [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] é uma coleção de instruções. Instruções [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] combinam expressões de forma que eles realizarem uma tarefa completa.  
  
 Uma instrução consiste em uma ou mais expressões, palavras-chave ou operadores (símbolos). Normalmente, uma instrução é gravada em uma única linha, embora uma instrução possa ser escrita em duas ou mais linhas. Além disso, duas ou mais instruções podem ser gravadas na mesma linha separando-as com ponto e vírgula. Em geral, cada nova linha começa uma nova instrução. Encerrar as instruções explicitamente é uma boa ideia. Você pode fazer isso com o ponto e vírgula (;), que é o caractere de terminação da instrução [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Aqui estão dois exemplos de instruções [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. As frases depois dos caracteres // são *comentários* explicativos no programa.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Um grupo de instruções [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] entre chaves ({}) é chamado de um *bloco*. Instruções agrupadas em um bloco geralmente podem ser tratadas como uma única instrução. Isso significa que você pode usar blocos na maioria dos locais em que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] espera uma única instrução. As exceções notáveis incluem os cabeçalhos dos loops **for** e `while`. Observe que as instruções individuais dentro de um bloco terminam com ponto e vírgula, mas o bloco propriamente dito não.  
  
 Em geral, os blocos são usados em funções e condicionais. Observe que, ao contrário do C++ e algumas outras linguagens, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] não considera um bloco como sendo um novo escopo; apenas funções criam um novo escopo.  
  
 No exemplo a seguir, a cláusula `else` contém um bloco de duas instruções entre chaves. O bloco é tratado como uma única instrução. Além disso, a própria função consiste em um bloco de instruções entre chaves. As instruções abaixo da função estão fora do bloco e, portanto, não fazem parte da definição da função.  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>Comentários  
 Um comentário [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] de linha única começa com um par de barras (//). Aqui está um exemplo de um comentário de linha única.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Um comentário [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] de várias linhas começa com uma barra e um asterisco (/*) e termina com o inverso (\*/).  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Se você tentar inserir um comentário de várias linhas dentro de outra, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpretará o comentário de várias linhas resultante de forma inesperada. O */ que marca o fim do comentário de várias linhas inserido é interpretado como o fim de todo o comentário várias linhas. Isso significa que o texto que segue o comentário de várias linhas inserido não será comentado; em vez disso, ele será interpretado como código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] e gerará erros de sintaxe.  
  
 É recomendável que você escreva todos os seus comentários como blocos de comentários de linha única. Isso permite que você comente grandes segmentos de código com um comentário de várias linhas mais tarde.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Atribuições e igualdade  
 O sinal de igual (=) é usado em instruções [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] para atribuir valores às variáveis: ele é o operador de atribuição. O operando à esquerda do operador = é sempre um Lvalue. Exemplos de Lvalues são:  
  
-   variáveis,  
  
-   elementos de matriz,  
  
-   propriedades do objeto.  
  
 O operando à direita do operador = é sempre um Rvalue. Rvalues pode ser um valor arbitrário de qualquer tipo, incluindo o valor de uma expressão. Aqui está um exemplo de uma instrução de atribuição [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anInteger = 3;  
```  
  
 O compilador [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta essa instrução como significando: "atribuir o valor 3 à variável **anInteger**," ou "**anInteger** assume o valor 3."  
  
 Verifique se você compreendeu a diferença entre o operador = (atribuição) e o operador == (igualdade). Quando você quiser comparar dois valores para saber se eles são iguais, use dois sinais de igual (==). Isso é discutido em detalhes em [Controlar o fluxo do programa](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="expressions"></a>Expressões  
 Um valor de expressão [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] pode ser de qualquer tipo [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] válido – um número, uma cadeia de caracteres, um objeto e assim por diante. As expressões mais simples são literais. Aqui estão alguns exemplos de expressões literais [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Expressões mais complicadas podem conter outras expressões, variáveis e chamadas de função. Você pode combinar expressões para criar expressões complexas usando operadores. São exemplos de operadores: `+` (adição), `-` (subtração) `*` (multiplicação) e `/` (divisão).  
  
 Aqui estão alguns exemplos de expressões complexas de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```
