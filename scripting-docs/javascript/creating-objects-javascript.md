---
title: Criando objetos (JavaScript) | Microsoft Docs
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
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="creating-objects-javascript"></a>Criando objetos (JavaScript)
Há várias maneiras para você pode criar seus próprios objetos em JavaScript. Você pode instanciar diretamente um [Objeto](../javascript/reference/object-object-javascript.md) e, em seguida, adicionar seus próprios métodos e propriedades. Ou pode usar a notação literal de objeto para definir o objeto. Você também pode usar uma função de construtor para definir um objeto. Para saber mais sobre como usar funções de construtor, consulte [Usando construtores para definir tipos](../javascript/advanced/using-constructors-to-define-types.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como instanciar um objeto e adicionar algumas propriedades. Nesse caso, apenas o objeto `pasta` tem as propriedades `grain`, `width` e `shape`.  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>Literais de objeto  
 Você também pode usar a notação literal de objeto para criar apenas uma instância de um objeto. O código a seguir mostra como instanciar um objeto usando a notação literal de objeto.  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Você também pode usar um literal de objeto dentro de um construtor.  
  
> [!CAUTION]
>  Os recursos descritos abaixo têm suporte apenas no [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Em [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)], você pode usar a sintaxe abreviada para criar um literal de objeto.  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 O exemplo a seguir mostra o uso da sintaxe abreviada para definir métodos em literais de objeto.  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 Você também pode definir nomes de propriedade dinamicamente em literais de objeto em [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)]. O exemplo de código a seguir cria um nome de propriedade para um objeto dinamicamente usando a sintaxe set.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 O exemplo de código a seguir cria um nome de propriedade para um objeto dinamicamente usando a sintaxe get.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 O exemplo de código a seguir cria uma propriedade computada usando a [sintaxe de função de seta](../javascript/functions-javascript.md) para acrescentar 42 ao nome da propriedade.  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```

