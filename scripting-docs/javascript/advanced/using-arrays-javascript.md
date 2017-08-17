---
title: Usando matrizes (JavaScript) | Microsoft Docs
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
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="using-arrays-javascript"></a>Usando matrizes (JavaScript)
Matrizes em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] são *esparsas*. Ou seja, se você tiver uma matriz com três elementos numerados como 0, 1 e 2, você poderá criar o elemento 50 sem se preocupar com os elementos de 3 a 49. Se a matriz tem uma variável de tamanho automático (consulte [objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md) para obter uma explicação de monitoramento automático de tamanho da matriz), a variável de tamanho é definida como 51, em vez de 4. Você pode criar matrizes em que não há intervalos na numeração de elementos, mas não é necessário fazer isso.  
  
 Em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], objetos e matrizes são quase idênticos uns aos outros. As duas principais diferenças são que objetos não matriz não têm uma propriedade de tamanho automático, enquanto matrizes não têm as propriedades e métodos de um objeto.  
  
## <a name="addressing-arrays"></a>Endereçamento de matrizes  
 Você pode endereçar matrizes usando colchetes ([]), conforme mostrado no exemplo a seguir. Os colchetes colocam um valor numérico ou uma expressão que retorna um número inteiro.  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>Objetos como matrizes associativas  
 Você geralmente usa o operador ponto "." para acessar as propriedades de um objeto. Por exemplo,  
  
```JavaScript  
myObject.aProperty  
```  
  
 Nesse caso, o nome da propriedade é um identificador. Você também pode acessar as propriedades de um objeto usando o operador de índice ([]). Nesse caso, você está tratando o objeto como uma *matriz associativa* na qual os valores de dados são associados com cadeias de caracteres. Por exemplo,  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 O operador de índice é mais comumente associado com o acesso a elementos de matriz. Quando ele é usado com objetos, o índice é um literal de cadeia de caracteres que representa o nome da propriedade.  
  
 Observe as diferenças importantes entre as duas maneiras de acessar as propriedades do objeto.  
  
1.  Um nome de propriedade tratado como um identificador (a sintaxe de ponto (.)) não pode ser manipulado como dados.  
  
2.  Um nome de propriedade tratado como um índice (a sintaxe de colchetes ([])) pode ser manipulado como dados.  
  
 Essa diferença é útil quando você não souber quais serão os nomes de propriedade até que o tempo de execução (por exemplo, quando você está construindo objetos com base na entrada do usuário). Para extrair todas as propriedades de uma matriz associativa, você deve usar o loop `for...in`.
