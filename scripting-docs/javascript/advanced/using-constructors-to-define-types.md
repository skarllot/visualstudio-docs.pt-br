---
title: Usar construtores para definir tipos | Microsoft Docs
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
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="using-constructors-to-define-types"></a>Usando construtores para definir tipos
Um construtor é uma função que instancia um tipo específico de [Objeto](../../javascript/objects-and-arrays-javascript.md). Você invoca um construtor com a palavra-chave **new**. Veja a seguir alguns exemplos de construtores com objetos JavaScript internos e objetos personalizados.  
  
## <a name="constructor-examples"></a>Exemplos de construtores  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 A função de construtor contém a palavra-chave **this**, que é uma referência a um objeto vazio recém-criado. Ela inicializa o novo objeto, criando propriedades e fornecendo valores iniciais a elas. O construtor retorna uma referência ao objeto que ele construiu.  
  
## <a name="writing-constructors"></a>Escrevendo construtores  
 Você pode criar objetos usando o operador **new** em conjunto com funções de construtor predefinidas, como **Object()**, **Date()** e **Function()**. Você também pode criar funções de construtor personalizadas que definem um conjunto de propriedades e métodos. Veja a seguir um exemplo de construtor personalizado.  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Ao invocar o construtor Circle, você fornece valores para o ponto central do círculo e o raio. O resultado é a geração de um objeto Circle que contém três propriedades. Vejamos como um objeto Circle seria instanciado.  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 O tipo de todos os objetos criados com um construtor personalizado é `object`. Há apenas seis tipos no JavaScript: `object`, `function`, `string`, `number`, `boolean` e `undefined`. Para obter mais informações, consulte [Operador TypeOf](../../javascript/reference/typeof-operator-decrementjavascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Usar o método bind](../../javascript/advanced/using-the-bind-method-javascript.md)
