---
title: "Variáveis (JavaScript) | Microsoft Docs"
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
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="variables-javascript"></a>Variáveis (JavaScript)
Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], uma variável contém um valor, como 5 ou "Olá". Quando você usa a variável, você se refere aos dados que ela representa, por exemplo, `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Você pode usar variáveis para armazenar, recuperar e manipular os valores que aparecem em seu código. Tente dar nomes significativos a suas variáveis para tornar mais fácil para outras pessoas entenderem o que seu código faz.  
  
## <a name="declaring-variables"></a>Declarando variáveis  
 A primeira vez que uma variável é exibida em seu script é a declaração dela. A primeira menção da variável define-a na memória, de modo que você pode consultá-la posteriormente no script. Você deve declarar variáveis antes de usá-los. Fazer isso usando a palavra-chave `var`.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Se você não inicializar a variável na instrução `var`, ela adquire automaticamente o valor `undefined`.  
  
## <a name="naming-variables"></a>Nomeando variáveis  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] é uma linguagem que diferencia maiúsculas e minúsculas. Isso significa que um nome de variável como **myCounter** é diferente do nome de variável **MYCounter**. Nomes de variável podem ser de qualquer tamanho. As regras para criar nomes de variável válidos são as seguintes:  
  
-   O primeiro caractere deve ser uma letra ASCII (maiúscula ou minúscula) ou um sublinhado (_). Observe que um número não pode ser usado como o primeiro caractere.  
  
-   Os caracteres subsequentes devem ser letras, números ou sublinhados (_).  
  
-   O nome da variável não pode ser uma [palavra reservada](../javascript/reference/javascript-reserved-words.md).  
  
 Aqui estão alguns exemplos de nomes de variável válidos:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Aqui estão alguns exemplos de nomes de variável inválidos:  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Quando você deseja declarar uma variável e inicializá-la, mas não deseja atribuir a ela nenhum valor específico, atribua a ela o valor `null`. Vejamos um exemplo.  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Se você declarar uma variável sem atribuir um valor a ela, ela terá o valor `undefined`. Vejamos um exemplo.  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 O valor `null` se comporta como o número 0, enquanto `undefined` se comporta como o valor especial `NaN` (não numérico). Se você comparar um valor `null` e um valor `undefined`, eles serão iguais.  
  
 Você pode declarar uma variável sem usar a palavra-chave `var` na declaração e atribuir um valor a ela. Esta é uma declaração implícita.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Você não pode usar uma variável que nunca foi declarada.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Coerção  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] é uma linguagem fracamente tipada, ao contrário de linguagens fortemente tipadas como C++. Isso significa que variáveis de JavaScript não têm nenhum tipo predeterminado. Em vez disso, o tipo de uma variável é o tipo do valor dela. Esse comportamento permite que você trate um valor como ele se fosse de um tipo diferente.  
  
 Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], você pode executar operações em valores de tipos diferentes sem gerar uma exceção. O interpretador [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] converte implicitamente ou *força*, um dos tipos de dados no tipo do outro e, em seguida, executa a operação. As regras de coerção de valores de cadeia de caracteres, números e boolianos são as seguintes:  
  
-   Se você adicionar um número e uma cadeia de caracteres, o número será forçado a tornar-se uma cadeia de caracteres.  
  
-   Se você adicionar um booliano e uma cadeia de caracteres, o booliano será forçado a tornar-se uma cadeia de caracteres.  
  
-   Se você adicionar um número e um booliano, o booliano será forçado a tornar-se um número.  
  
 No exemplo a seguir, um número adicionado a uma cadeia de caracteres resulta em uma cadeia de caracteres.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Cadeias de caracteres são automaticamente convertidas em números equivalentes para fins de comparação. Para converter explicitamente de uma cadeia de caracteres em um inteiro, use a [função parseInt](../javascript/reference/parseint-function-javascript.md). Para converter explicitamente de uma cadeia de caracteres em um número, use a [função parseFloat](../javascript/reference/parsefloat-function-javascript.md).
