---
title: Propriedades de dados e propriedades de acessadores | Microsoft Docs
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
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="data-properties-and-accessor-properties"></a>Propriedades de dados e propriedades de acessador
Esta seção inclui todas as informações que provavelmente serão necessárias sobre propriedades de dados e as propriedades de acessadores.  
  
### <a name="data-properties"></a>Propriedades de dados  
 Um *propriedade dados* é uma propriedade que pode obter e definir um valor. As propriedades de dados contêm as propriedades `value` e `writable` nos seus descritores.  
  
 A tabela a seguir lista os atributos para um descritor de propriedade de dados.  
  
|Atributo de descritor de dados|Descrição|Padrão|  
|-------------------------------|-----------------|-------------|  
|`value`|O valor atual da propriedade.|`undefined`|  
|`writable`|`true` ou `false`. Se `writable` é definido como `true`, o valor da propriedade pode ser modificado.|`false`|  
|`enumerable`|`true` ou `false`. Se `enumerable` é definido como `true`, a propriedade pode ser enumerada por uma instrução `for...in`.|`false`|  
|`configurable`|`true` ou `false`. Se `configurable` é definido como `true`, atributos de propriedade podem ser alterados e a propriedade pode ser excluída.|`false`|  
  
 Se o descritor não tiver um atributo `value`, `writable`, `get` ou `set` e o nome da propriedade especificada não existir, uma propriedade de dados será adicionada.  
  
 Quando o atributo `configurable` é `false` e `writable` é `true`, os atributos `value` e `writable` podem ser alterados.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>Propriedades de Dados adicionadas sem o uso de defineProperty  
 Se você adicionar uma propriedade de dados sem usar as funções `Object.defineProperty`, `Object.defineProperties` ou `Object.create`, os atributos `writable`, `enumerable` e `configurable` serão todos definidos para `true`. Depois que a propriedade é adicionada, você pode modificá-la usando a função `Object.defineProperty`.  
  
 Você pode usar as seguintes maneiras para adicionar uma propriedade de dados:  
  
-   Um operador de atribuição (=), como em `obj.color = "white";`  
  
-   Um literal de objeto, como em `obj = { color: "white", height: 5 };`  
  
-   Uma função de construção, conforme descrito em [Usando construtores para definir tipos](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### <a name="accessor-properties"></a>Propriedades de acessador  
 Um *propriedade do acessador* chama uma função fornecida pelo usuário sempre que o valor da propriedade é definido ou recuperado. O descritor de uma propriedade de acessador tem um atributo `get`, um atributo `set` ou ambos.  
  
 A tabela a seguir lista os atributos para um descritor de propriedade de acessador.  
  
|Atributo de descritor de acessador|Descrição|Padrão|  
|-----------------------------------|-----------------|-------------|  
|`get`|Uma função que retorna o valor da propriedade. A função não tem parâmetros.|`undefined`|  
|`set`|Uma função que define o valor da propriedade. Ele tem um parâmetro que contém o valor a ser atribuído.|`undefined`|  
|`enumerable`|`true` ou `false`. Se `enumerable` é definido como `true`, a propriedade pode ser enumerada por uma instrução `for...in`.|`false`|  
|`configurable`|`true` ou `false`. Se `configurable` é definido como `true`, atributos de propriedade podem ser alterados e a propriedade pode ser excluída.|`false`|  
  
 Quando um acessador `get` não está definido e é feita uma tentativa de acessar o valor da propriedade, o valor `undefined` é retornado. Quando um acessador `set` não está definido e é feita uma tentativa de atribuir um valor para a propriedade de acessador, nada ocorre.  
  
### <a name="property-modifications"></a>Modificações de propriedade  
 Se o objeto já tem uma propriedade com o nome especificado, os atributos da propriedade são modificados. Quando você modifica a propriedade, os atributos que não são especificados no descritor de permanecem os mesmos.  
  
 Se o atributo `configurable` de uma propriedade existente é `false`, a única modificação permitida é alterar o atributo `writable` de `true` para `false`.  
  
 Você pode alterar uma propriedade de dados para uma propriedade de acessador e vice-versa. Se você fizer isso, os atributos `configurable` e `enumerable` que não são especificados no descritor serão preservados na propriedade. Outros atributos que não são especificados no descritor são definidos para os respectivos valores padrão.  
  
 Você pode definir incrementalmente propriedades de acessador configuráveis por meio de várias chamadas para a função `Object.defineProperty`. Por exemplo, uma chamada `Object.defineProperty` pode definir apenas um acessador `get`. Uma chamada posterior no mesmo nome de propriedade pode definir um acessador `set`. A propriedade teria ambos um acessador `get` e acessador `set`.  
  
 Para obter um objeto de descritor que se aplica a uma propriedade existente, você pode usar a [função Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Você pode usar a [função Object.seal](../../javascript/reference/object-seal-function-javascript.md) e [função Object.freeze](../../javascript/reference/object-freeze-function-javascript.md) para impedir a modificação dos atributos da propriedade.
