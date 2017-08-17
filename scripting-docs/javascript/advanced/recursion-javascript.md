---
title: "Recursão (JavaScript) | Microsoft Docs"
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
- functions, recursive function calls
- recursive procedures
- function calls, recursive
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 06735c244ed6bd3c8d9abe59123f9f961e6f1847
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="recursion-javascript"></a>Recursão (JavaScript)
Recursão é uma técnica de programação importante, em que uma função chama a si mesma.  
  
## <a name="an-example-of-recursion"></a>Um exemplo de recursão  
 Um exemplo é o cálculo de fatoriais. O fatorial de um número *n* é calculado multiplicando-se 1 \* 2 \* 3 \*... *n*. O exemplo a seguir mostra como calcular fatoriais iterativamente, ou seja, usando um loop `while` no qual o resultado é calculado.  
  
```JavaScript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 Você pode tornar o exemplo recursivo de modo muito simples. Em vez de usar um loop `while` para calcular o valor, você pode simplesmente chamar `factorial` novamente, passando o próximo valor mais baixo. A recursão para quando o valor é 1.  
  
```JavaScript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```
