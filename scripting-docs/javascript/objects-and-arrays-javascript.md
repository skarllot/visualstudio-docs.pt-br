---
title: Objetos e matrizes (JavaScript) | Microsoft Docs
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
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6776701ba108ae0ecefc2331c2b12272e0c1be19
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="objects-and-arrays-javascript"></a>Objetos e matrizes (JavaScript)
Objetos [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] são coleções de propriedades e métodos. Um método é uma função que é um membro de um objeto. Uma propriedade é um valor ou conjunto de valores (na forma de uma matriz ou objeto) que é um membro de um objeto. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dá suporte a quatro tipos de objetos:  
  
-   Objetos intrínsecos, assim como `Array` e `String`.  
  
-   Objetos que você cria.  
  
-   Objetos de host, tais como `window` e `document`.  
  
-   Objetos ActiveX.  
  
## <a name="expando-properties-and-methods"></a>Propriedades e Métodos Expando  
 Todos os objetos em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] dão suporte a propriedades e métodos expando, que podem ser adicionados e removidos em tempo de execução. Essas propriedades e métodos podem ter qualquer nome e podem ser identificados por números. Se o nome da propriedade ou método é um identificador simples, ele pode ser gravado após o nome do objeto com um ponto, assim como `myObj.name`, `myObj.age` e `myObj.getAge` no código a seguir:  
  
```JavaScript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Se o nome da propriedade ou método não é um identificador simples ou é desconhecido no momento em que você escreve o script, você pode usar uma expressão dentro de colchetes para indexar a propriedade. Os nomes das propriedades expando em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] são convertidos em cadeias de caracteres antes de serem adicionados ao objeto.  
  
```JavaScript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Para obter informações sobre como criar um objeto de uma definição, consulte [Criando objetos](../javascript/creating-objects-javascript.md).  
  
## <a name="arrays-as-objects"></a>Matrizes como Objetos  
 Em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], objetos e matrizes são manipulados de maneira quase idêntica, porque as matrizes são simplesmente um tipo especial de objeto. Tanto objetos quanto matrizes podem ter propriedades e métodos.  
  
 As matrizes têm uma propriedade `length`, mas os objetos não. Quando você atribui um valor a um elemento de uma matriz cujo índice é maior do que seu tamanho (por exemplo, `myArray[100] = "hello"`), a propriedade `length` é automaticamente aumentada para o novo tamanho. Da mesma forma, se você tornar a propriedade `length` menor, qualquer elemento cujo índice estiver fora do tamanho da matriz será excluído.  
  
```JavaScript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Matrizes fornecem métodos para iterar pelos membros e manipulá-los. O exemplo a seguir mostra como obter as propriedades de objetos armazenados em uma matriz.  
  
```JavaScript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## <a name="multi-dimensional-arrays"></a>Matrizes Multidimensionais  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] não dá suporte direto a matrizes multidimensionais, mas você pode obter o comportamento de matrizes multidimensionais armazenando matrizes dentro dos elementos de outra matriz. (Você pode armazenar qualquer tipo de dados dentro de elementos da matriz, incluindo outras matrizes). Por exemplo, o código a seguir cria uma tabela de multiplicação para os números até 5.  
  
```JavaScript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```
