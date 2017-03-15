---
title: "&lt; Valor &gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "< Valor > marca XML JavaScript"
  - "marca XML de valor JavaScript"
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Valor &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica informações sobre a documentação para `get` e `set` funciona para ECMAScript 3 propriedades.  
  
## Sintaxe  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### Parâmetros  
 `type`  
 Opcional.  O tipo de dados da propriedade.  O tipo pode ser um dos seguintes:  
  
-   Um tipo de linguagem ECMAScript que está na especificação de ECMAScript 5, como `Number` e `Object`.  
  
-   O objeto DOM, como `HTMLElement`, `Window`, e `Document`.  
  
-   Uma função de construtor de JavaScript.  
  
 `integer`  
 Opcional.  Se `type` é `Number`, especifica se a propriedade é um número inteiro.  Defina a `true` para indicar que a propriedade é um inteiro; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `domElement`  
 Opcional.  Esse atributo é substituído; o atributo de `type` tem precedência sobre este atributo.  Esse atributo especifica se a propriedade documentada é um elemento DOM.  Defina a `true` para especificar qual propriedade é um elemento DOM; se não, defina a `false`.  Se o atributo de `type` não está definido e `domElement` é definido como `true`, o IntelliSense trata a propriedade documentada como `HTMLElement` ao executar a instrução.  
  
 `mayBeNull`  
 Opcional.  Especifica se a propriedade documentada pode ser definida para nulo.  Defina a `true` para indicar que a propriedade pode ser definida para nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementType`  
 Opcional.  Se `type` é `Array`, esse atributo especifica o tipo dos elementos da matriz.  
  
 `elementInteger`  
 Opcional.  Se `type` é `Array` e `elementType` é `Number`, esse atributo especifica se os elementos na matriz são números inteiros.  Defina a `true` para indicar que os elementos na matriz são números inteiros; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementDomElement`  
 Opcional.  Esse atributo é substituído; o atributo de `elementType` tem precedência sobre este atributo.  Se `type` é `Array`, esse atributo especifica se os elementos na matriz são elementos DOM.  Defina a `true` para especificar que os elementos são elementos DOM; se não, defina a `false`.  Se o atributo de `elementType` não está definido e `elementDomElement` é definido como `true`, o IntelliSense trata cada elemento na matriz como `HTMLElement` ao executar a instrução.  
  
 `elementMayBeNull`  
 Opcional.  Se `type` é `Array`, especifica se os elementos na matriz podem ser definidos como nulo.  Defina a `true` para indicar que os elementos na matriz podem ser definidos como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `locid`  
 Opcional.  O identificador para informações sobre localização da propriedade.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado no elemento de [\< loc \>](../ide/loc-javascript.md) .  
  
 `description`  
 Opcional.  Uma descrição da propriedade.  
  
## Comentários  
 ECMAScript 5 propriedades usa o elemento de [\< resumo \>](../ide/summary-javascript.md) .  
  
 Use o elemento de `<value>` imediatamente antes de função de `get` ou de `set` .  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar o elemento de `<value>` em uma função de `get` .  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)