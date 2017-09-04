---
title: Controlando o fluxo do programa (JavaScript) | Microsoft Docs
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
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="controlling-program-flow-javascript"></a>Controlando o fluxo de programas (JavaScript)
Normalmente, as instruções em um script [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] são executadas uma após a outra, na ordem em que elas são gravadas. Isso é chamado de execução sequencial e é a direção padrão de fluxo de programa.  
  
 Uma alternativa à execução sequencial transfere o fluxo de programa para outra parte do seu script. Ou seja, outra instrução é executada em vez da próxima instrução na sequência.  
  
 Para tornar um script útil, essa transferência de controle deve ser feita de maneira lógica. Transferência de controle do programa baseia-se em uma decisão, cujo resultado é uma instrução de verdade (retornando um valor booliano **true** ou **false**). Você cria uma expressão e então testa se o resultado dela é verdadeiro. Há dois tipos principais de estruturas de programa que fazem isso.  
  
 A primeira é a estrutura de seleção. Você pode usá-la para especificar cursos alternativos do fluxo do programa, criando uma junção em seu programa (como uma bifurcação de uma estrada). Há quatro estruturas de seleção disponíveis em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   a estrutura de seleção única (**if**),  
  
-   a estrutura de seleção dupla (**if/else**),  
  
-   o operador ternário embutido `?:`  
  
-   a estrutura de seleção múltipla (`switch`).  
  
 O segundo tipo de estrutura de controle do programa é a estrutura de repetição. Você a usa para especificar que uma ação deve ser repetida enquanto uma condição permanece verdadeira. Quando as condições da instrução de controle tiverem sido atendidas (geralmente após um número específico de iterações), o controle passará para a próxima instrução além da estrutura de repetição. Há quatro estruturas de repetição disponíveis em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   a expressão é testada na parte superior do loop (`while`),  
  
-   a expressão é testada na parte inferior do loop (**do/while**),  
  
-   operar em cada uma das propriedades de um objeto (**for/in**).  
  
-   repetição controlada por contador (**for**).  
  
 Você pode criar scripts bastante complexos aninhando e empilhando estruturas de controle de seleção e de repetição.  
  
 Uma terceira forma de fluxo de programa estruturado é fornecida pela manipulação de exceções, que não é abordada neste documento.  
  
## <a name="using-conditional-statements"></a>Usando instruções condicionais  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dá suporte às instruções condicionais **if** e [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md). Em instruções **if**, uma condição é testada e, se passa no teste, o código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] relevante é executado. Na instrução `if...else`, um código diferente é executado se a condição falha no teste. A forma mais simples de uma instrução **if** pode ser gravada em uma linha, mas instruções **if** e `if...else` de várias linhas são muito mais comuns.  
  
 Os exemplos a seguir demonstram sintaxes que você pode usar com instruções **if** e `if...else`. O primeiro exemplo mostra o tipo mais simples de teste booliano. Se (e somente se) o item entre os parênteses retorna (ou pode ser forçado a retornar) **true**, a instrução ou bloco de instruções após a **if** é executado.  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>Operador condicional  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] também dá suporte a um formulário condicional implícito. Ele usa um ponto de interrogação após a condição a ser testada (em vez da palavra **if** antes da condição). Ele também especifica duas alternativas, uma a ser usada se a condição for atendida e a outra se não for. Dois-pontos devem separar essas alternativas.  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Se você tiver várias condições a serem testadas juntas e você sabe que uma tem maior probabilidade de aprovação ou reprovação que as outras, você poderá usar um recurso chamado 'avaliação de circuito pequeno' para acelerar a execução do script. Quando [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] avalia uma expressão lógica, ela avalia apenas o número de subexpressões necessário para obter um resultado.  
  
 Por exemplo, se você tiver uma expressão AND como ((x == 123) && (y == 6)), [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] primeiro verifica se x é 123. Se não for, a expressão inteira não pode ser true, mesmo que y seja igual a 6. Portanto, o teste de y nunca é feito e [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] retorna o valor **false**.  
  
 Da mesma forma, se apenas uma das várias condições deve ser **true** (usando o operador &#124;&#124;), o teste é interrompido assim que uma condição qualquer passa no teste. Isso é eficaz se as condições a serem testadas envolvem a execução de chamadas de função ou outras expressões complexas. Com isso em mente, quando você escreve expressões Or, coloque as condições com maior probabilidade de serem **true** primeiro. Quando você escreve expressões And, coloque as condições com maior probabilidade de serem **false** primeiro.  
  
 Uma vantagem de criar seu script dessa maneira é que **runsecond()** não será executada no exemplo a seguir se **runfirst()** retornar 0.  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>Usando loops  
 Há várias maneiras de executar uma instrução ou bloco de instruções repetidamente. Em geral, a execução repetitiva é chamada de *loop* ou *iteração*. Uma iteração é simplesmente uma única execução de um loop. Normalmente, ela é controlada por um teste de uma variável, no qual o valor dela é alterado sempre que o loop é executado. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dá suporte a quatro tipos de loop: loops [for](../javascript/reference/for-statement-javascript.md), loops [for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), loops [while](../javascript/reference/while-statement-javascript.md), loops [do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md).  
  
## <a name="using-for-loops"></a>Usando loops for  
 A instrução **for** especifica uma variável de contador, uma condição de teste e uma ação que atualiza o contador. Antes de cada iteração do loop, a condição é testada. Se o teste for bem-sucedido, o código dentro do loop será executado. Se o teste falha, o código dentro do loop não é executado e o programa continua na primeira linha de código imediatamente após o loop. Depois que o loop é executado, a variável de contador é atualizada antes do início da próxima iteração.  
  
 Se a condição de loop nunca for atendida, o loop nunca será executado. Se a condição de teste sempre for atendida, o resultado será um loop infinito. Embora a primeira dessas situações possa ser desejável em certos casos, a última raramente é, portanto, cuidado ao escrever suas condições de loop.  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>Usando for... em loops  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fornece um tipo especial de loop para percorrer todas as propriedades definidas pelo usuário de um [objeto](../javascript/objects-and-arrays-javascript.md) ou todos os elementos de uma matriz. O contador de loops em um loop `for...in` é uma cadeia de caracteres, não é um número. Ele contém o nome da propriedade atual ou o índice do elemento de matriz atual.  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Embora loops `for...in` se pareçam com loops `For Each...Next` do VBScript, eles não funcionam da mesma maneira. O [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**loop for... in** itera pelas propriedades de objetos [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. O loop **For Each...Next** do VBScript itera pelos itens em uma coleção. Para executar um loop em coleções em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], você precisa usar o [objeto enumerador](../javascript/reference/enumerator-object-javascript.md) ou, se presente, o método `forEach` do objeto da coleção. Embora alguns objetos como aqueles no Internet Explorer deem suporte a ambos o loop **For Each...Next** do VBScript e o loop [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**for...in**, a maioria dos objetos não dão.  
  
## <a name="using-while-loops"></a>Usando loops while  
 Um loop `while` é semelhante a um loop **for**. A diferença é que um loop `while` não tem uma expressão de atualização ou variável de contador interna. Se você deseja controlar a execução repetitiva de uma instrução ou bloco de instruções mas precisa de uma regra mais complexa do que simplesmente "executar esse código n vezes", use um loop `while`. O exemplo a seguir usa o modelo de objeto do Internet Explorer e um loop `while` para fazer uma pergunta simples ao usuário.  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  Já que loops `while` não têm variáveis de contador interno explícitas, eles são mais vulneráveis a loop infinito do que os outros tipos de loops. Além disso, já que não é necessariamente fácil descobrir onde e quando a condição de loop é atualizada, é fácil escrever um loop `while` no qual a condição nunca é atualizada. Por esse motivo, você deve ter cuidado ao criar loops `while`.  
  
 Conforme observado acima, há também um loop **do...while** em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] que é semelhante ao loop while, exceto que é garantido que ele sempre seja executado pelo menos uma vez, desde que a condição seja testada no final do loop, em vez de no início. Por exemplo, o loop acima pode ser reescrito como:  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>Usando as instruções break e continue  
 Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], a instrução [break](../javascript/reference/break-statement-javascript.md) é usada para interromper a execução de um loop se alguma condição é atendida. (Observe que **break** também é usada para encerrar um bloco `switch`). A instrução [continue](../javascript/reference/continue-statement-javascript.md) pode ser usada para ir imediatamente para a próxima iteração, ignorando o restante do bloco de código e simultaneamente atualizando a variável de contador se o loop é um loop **for** ou `for...in`.  
  
 O exemplo a seguir dá sequência ao exposto no exemplo anterior para usar as instruções **break** e **continue** para controlar o loop.  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```
