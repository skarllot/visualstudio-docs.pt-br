---
title: "Coleções (JavaScript) | Microsoft Docs"
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
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: aa14730fffbf7c2747f15243590be89dc01a7ceb
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="collections-javascript"></a>Coleções (JavaScript)
É possível usar os objetos de coleção [Map](../../javascript/reference/map-object-javascript.md), [Set](../../javascript/reference/set-object-javascript.md) e [WeakMap](../../javascript/reference/weakmap-object-javascript.md) para armazenar valores e objetos. Esses objetos fornecem métodos convenientes para adicionar e recuperar membros usando uma chave ou um valor em vez de um índice. Para acessar membros de uma coleção usando um índice, use um objeto `Array`. Para obter mais informações, consulte [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  `Map`, `Set` e `WeakMap` não são aceitos em versões do navegador anteriores ao Internet Explorer 11. Para obter mais informações sobre o suporte de versão, consulte [Informações de versão](../../javascript/reference/javascript-version-information.md).  
  
## <a name="using-collections"></a>Usando coleções  
 Os objetos `Map` e `WeakMap` armazenam pares chave/valor e permitem que você adicione, remova e recupere membros usando a chave. A chave e o valor podem ser de qualquer tipo. O objeto `Set` armazena valores de qualquer tipo.  
  
 Os objetos `Map` e `Set` permitem que você enumere os membros da coleção usando o método `forEach` e verifique o tamanho da coleção usando o método `size`. O objeto `WeakMap`, por outro lado, não é enumerável. Para essa coleção, as referências de chave são mantidas "fracas". Use `WeakMap` se você desejar que o coletor de lixo determine se o aplicativo precisará reter cada membro da coleção na memória. Por exemplo, isso pode ser útil em cenários de cache em que os objetos armazenados em cache são muito grandes e você não deseja armazenar desnecessariamente objetos na memória. Em alguns cenários, você pode usar esse objeto para evitar vazamentos de memória.  
  
 O exemplo a seguir mostra como usar o objeto `Map`. Nesse exemplo, você acessa os membros usando `get` e `forEach`. A função de retorno de chamada no `forEach` pode ter até três parâmetros, os quais fornecem o valor do elemento da coleção atual, a chave do elemento atual e o próprio objeto da coleção.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 O uso de `WeakMap` é semelhante a `Map`, exceto que você pode recuperar apenas membros usando `get`. Para ver um exemplo, consulte o objeto [WeakMap](../../javascript/reference/weakmap-object-javascript.md).  
  
 O exemplo a seguir mostra como usar o objeto `Set`. Nesse exemplo, a função de retorno de chamada aceita um parâmetro, que é o valor do elemento atual da coleção.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [JavaScript avançado](../../javascript/advanced/advanced-javascript.md)
