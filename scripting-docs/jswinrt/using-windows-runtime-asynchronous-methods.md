---
title: "Usar métodos assíncronos do Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="using-windows-runtime-asynchronous-methods"></a>Usar métodos assíncronos do Windows Runtime
Muitos métodos do Tempo de Execução do Windows, especialmente os que demoram muito para serem concluídos, são assíncronos. Esses métodos normalmente retornam uma ação ou uma operação assíncrona (por exemplo, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` ou `Windows.Foundation.IAsyncOperationWithProgress`). Esses métodos são representados em JavaScript pelo padrão [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434). Ou seja, eles retornam um objeto Promise com uma função [then](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx) para a qual você deve fornecer uma função `completed` que identifique o resultado caso a operação seja bem-sucedida. Se não quiser fornecer um manipulador de erros, use a função [done](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) em vez da função `then`.  
  
> [!IMPORTANT]
>  Os recursos de Tempo de Execução do Windows não estão disponíveis para aplicativos executados no Internet Explorer.  
  
## <a name="examples-of-asynchronous-methods"></a>Exemplos de métodos assíncronos  
 No exemplo a seguir, a função `then` utiliza um parâmetro que representa o valor completo do método `createResourceAsync`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 Nesse caso, se o método `createResourceAsync` falhar, ele retornará uma promessa no estado de erro, mas não lançará uma exceção. Você pode identificar um erro usando a função `then` da seguinte forma.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Se não quiser identificar o erro explicitamente, mas quiser lançar uma exceção, use a função `done` em seu lugar.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Você também pode exibir o andamento em relação à conclusão usando uma terceira função.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Para obter mais informações sobre programação assíncrona, consulte [Programação assíncrona em JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>Consulte também  
 [Usar o Windows Runtime em JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
