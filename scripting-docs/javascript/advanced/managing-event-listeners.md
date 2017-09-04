---
title: Gerenciar ouvintes de eventos | Microsoft Docs
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
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="managing-event-listeners"></a>Gerenciando ouvintes de eventos
Se o tempo de vida de um elemento ou objeto DOM é diferente do tempo de vida do ouvinte de eventos associado, talvez seja necessário usar o método [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx) para evitar perdas de memória.  
  
## <a name="event-listeners-and-object-scope"></a>Ouvintes de eventos e escopo do objeto  
 O exemplo de código a seguir mostra um código que pode causar perda de memória quando a função `dataObjFactory()` for chamada. Nesse código, o ouvinte de eventos é registrado para cada objeto de dados a cada vez que um novo objeto desse tipo é criado. Para disponibilizar o objeto de dados atual no manipulador de eventos `dataReady()`, usa-se [o método bind (Função)](../../javascript/reference/bind-method-function-javascript.md) em `addEventListener`.  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 O ouvinte de cada objeto de dados é registrado com o objeto `document`, que tem um tempo de vida diferente do tempo dos objetos de dados. O ouvinte de eventos registrado para cada objeto de dados evita a coleta de lixo enquanto o objeto `document` permanece no escopo. Em alguns padrões modernos de design do JavaScript, o objeto permanece no escopo durante o tempo de vida do aplicativo da Web. Para evitar a perda de memória, `removeEventListener` é chamado na função `dataObjFactory`. No entanto, esse código falha porque `removeEventListener` não foi chamado na versão associada do manipulador de eventos que é retornado pela função `bind`.  
  
 Para corrigir esse código disponibilizar os objetos de dados para coleta de lixo, primeiro armazene uma referência à versão associada do manipulador de eventos, como mostra esse código, e transmita a referência armazenada para `addEventListener`. Este é o código corrigido para `DataObject`:  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Por fim, você precisa chamar `removeEventListener` na referência armazenada (`handlerRef`) da função associada. Este é o código corrigido para `dataObjFactory`:  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Agora a chamada de `removeEventListener` funciona e é possível coletar lixo nos objetos de dados desnecessários, mesmo enquanto o objeto `document` ainda estiver no escopo.
