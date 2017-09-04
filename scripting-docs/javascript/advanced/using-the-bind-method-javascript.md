---
title: "Usando o método bind (JavaScript) | Microsoft Docs"
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
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 8c49f6e8c5606845f41cc947029ac9405f97665f
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="using-the-bind-method-javascript"></a>Usando o método bind (JavaScript)
O método de JavaScript `bind` possui vários usos. Normalmente, ele é usado para preservar o contexto de execução para uma função que executa em outro contexto. `bind` cria uma nova função com o mesmo corpo da função original. O primeiro argumento passado para `bind` especifica o valor da palavra-chave `this` na função associada. Você também pode passar argumentos opcionais adicionais para `bind`. Para obter exemplos de usos adicionais, consulte o [Método bind (Function)](../../javascript/reference/bind-method-function-javascript.md). Para um exemplo de como usar `bind` para aplicar parcialmente as funções, consulte [Padrões e dicas de programação assíncrona no Hilo JavaScript (Windows Store)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Preservando o contexto de execução via bind  
 A função `bind` é muitas vezes usada na adição de ouvintes de evento. No exemplo de código a seguir, `bind` é usada para preservar o contexto do objeto atual (`DataObject`). O objeto de dados é passado para `bind` usando a palavra-chave `this`, a qual fornece acesso às propriedades de objetos de dados e funções quando o manipulador de eventos (`dataReadyHandler`) é executado. Para ilustrar como `bind` funciona, esse código cria um evento personalizado.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);  
}  
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Se você comentar a linha de código que usa `bind`, descomentar a linha de código que chama `addEventListener` sem `bind` e executar o código novamente, a função `dataReadyHandler` falhará. Por exemplo, em `dataReadyHander`, `this.name` será indefinido e `this.data()` resultará em um erro porque o objeto `this` não se refere mais ao objeto de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Método bind (Function)](../../javascript/reference/bind-method-function-javascript.md)
