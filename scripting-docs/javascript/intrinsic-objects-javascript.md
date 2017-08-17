---
title: "Objetos intrínsecos (JavaScript) | Microsoft Docs"
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
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="intrinsic-objects-javascript"></a>Objetos intrínsecos (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fornece objetos intrínsecos (ou "internos"). Eles são os objetos `Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **Math**, **Number**, `Object`, `RegExp` e `String`. Os objetos intrínsecos têm métodos, funções, propriedades e constantes associados, que são descritos detalhadamente na [referência de linguagem](../javascript/reference/javascript-reference.md).  
  
## <a name="array-object"></a>Objeto Array  
 Os subscritos de uma matriz podem ser considerados como propriedades de um objeto e são referidos por seu índice numérico. Observe as propriedades nomeadas adicionadas a uma matriz não podem ser indexadas por número; elas são separadas dos elementos da matriz.  
  
 Para criar uma nova matriz, use o operador **new** e o [construtor](../javascript/reference/constructor-property-object-javascript.md) **Array()**, conforme o exemplo a seguir.  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 Quando você cria uma matriz usando a palavra-chave `Array`, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] inclui uma propriedade **length**, que registra o número de entradas. Se você não especificar um número, o comprimento é definido como 0 e a matriz não tem entradas. Se você especificar um número, o comprimento é definido conforme esse número. Se você especificar mais de um parâmetro, os parâmetros são usados como entradas na matriz. Além disso, o número de parâmetros é atribuído à propriedade de comprimento, como no exemplo a seguir, que é equivalente ao exemplo anterior.  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] altera automaticamente o valor de **length** quando você adiciona elementos a uma matriz que criou com a palavra-chave `Array`. Índices de matriz em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sempre começam com 0, não 1. Portanto, a propriedade length é sempre um número maior que o maior índice da matriz.  
  
## <a name="string-object"></a>Objeto String  
 Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], você pode tratar cadeias de caracteres (e números) como se fossem objetos. O [Objeto string](../javascript/reference/string-object-javascript.md) tem determinados métodos internos que você pode usar com suas cadeias de caracteres. Um deles é o [Método substring](../javascript/reference/substring-method-string-javascript.md), que retorna parte da cadeia de caracteres. Ele usa dois números como seus argumentos.  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Outra propriedade do objeto `String` é **length**. Esta propriedade contém o número de caracteres na cadeia de caracteres (0 para uma cadeia vazia). Trata-se de um valor numérico, que pode ser usado diretamente em cálculos.  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Objeto Math  
 O objeto **Math** tem um número de funções e constantes predefinidas. As constantes são números específicos. Um desses números específicos é o valor de pi (aproximadamente 3,14159...). É a constante **Math.PI**, mostrada no exemplo a seguir.  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 Uma das funções internas do objeto **Math** é o método de exponenciação ou `Math.pow`, que eleva um número a uma potência especificada. O exemplo a seguir usa pi e a exponenciação para calcular o volume de uma esfera.  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Objeto Date  
 O objeto `Date` pode ser usado para representar datas e horas arbitrárias, para obter a data atual do sistema e para calcular as diferenças entre as datas. Ele tem várias propriedades e métodos, todos predefinidos. Em geral, o objeto `Date` fornece o dia da semana, o mês, dia e ano, bem como o tempo em horas, minutos e segundos. Essas informações se baseiam no número de milissegundos desde 1º de janeiro de 1970, 00:00:00.000 GMT, que é hora de Greenwich (o termo preferido é UTC ou "Horário Coordenado Universal", que se refere aos sinais emitidos pelo Padrão Mundial de Horários). [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] pode manipular datas que estão no intervalo aproximado de 250.000 A.C. a 255.000 D.C.  
  
 Para criar um novo objeto `Date`, use o operador **new**, conforme mostrado no exemplo a seguir.  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Objeto Number  
 Além das constantes numéricas especiais (`PI`, por exemplo) que estão disponíveis no objeto **Math**, várias outras constantes estão disponíveis em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] por meio do objeto **Number**.  
  
|Constante|Descrição|  
|--------------|-----------------|  
|Number. MAX_VALUE|O maior número possível, cerca de 1,79E + 308; pode ser positivo ou negativo. (O valor varia ligeiramente de um sistema para outro.)|  
|Number. MIN_VALUE|O menor número possível, cerca de 5.00E-324; pode ser positivo ou negativo. (O valor varia ligeiramente de um sistema para outro.)|  
|Number.NaN|Valor numérico especial, "não é um número".|  
|Number.POSITIVE_INFINITY|Qualquer valor positivo maior que o maior número positivo (Number. MAX_VALUE) é convertido automaticamente para esse valor; representado como infinito.|  
|Number.NEGATIVE_INFINITY|Qualquer valor mais negativo que o maior número negativo (-Number. MAX_VALUE) é convertido automaticamente para esse valor; representado como -infinito.|  
  
 **Number.NaN** é uma constante especial que é definida como "não é um número". Uma tentativa de analisar uma cadeia de caracteres que não pode ser analisada como um número retorna **Number. NaN**. `NaN` compara valores desiguais a qualquer número e a si mesmo. Para testar um resultado `NaN`, não compare com **Number.NaN**; em vez disso, use a função **isNaN()**.  
  
## <a name="json-object"></a>Objeto JSON  
 O JSON é um formato de troca de dados leve baseado em um subconjunto da notação literal de objetos da linguagem JavaScript.  
  
 O objeto JSON fornece duas funções para converter para e do formato de texto JSON. A função [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) serializa objetos e matrizes em texto JSON. A função [JSON.parse](../javascript/reference/json-parse-function-javascript.md) desfaz a serialização do texto JSON para produzir objetos na memória. Para obter mais informações, consulte [Uma introdução à JSON (JavaScript Object Notation) em JavaScript e .NET](http://go.microsoft.com/fwlink/?LinkId=124098).  
  
## <a name="see-also"></a>Consulte também  
 [Objetos JavaScript](../javascript/reference/javascript-objects.md)
