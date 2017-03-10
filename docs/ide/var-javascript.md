---
title: "&lt; Var &gt; (JavaScript) | Microsoft Docs"
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
  - "< Var > marca XML JavaScript"
  - "marca XML var JavaScript"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Var &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica informações sobre a documentação para uma variável.  
  
## Sintaxe  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### Parâmetros  
 `type`  
 Opcional.  O tipo de dados da variável.  O tipo pode ser um dos seguintes:  
  
-   Um tipo de linguagem ECMAScript que está na especificação de ECMAScript 5, como `Number` e `Object`.  
  
-   O objeto DOM, como `HTMLElement`, `Window`, e `Document`.  
  
-   Uma função de construtor de JavaScript.  
  
 `integer`  
 Opcional.  Se `type` é `Number`, especifica se a variável é um número inteiro.  Defina a `true` para indicar que a variável é um inteiro; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `domElement`  
 Opcional.  Esse atributo é substituído; o atributo de `type` tem precedência sobre este atributo.  Esse atributo especifica se a variável documentado é um elemento DOM.  Defina a `true` para especificar que a variável é um elemento DOM; se não, defina a `false`.  Se o atributo de `type` não está definido e `domElement` é definido como `true`, o IntelliSense trata a variável documentado como `HTMLElement` ao executar a instrução.  
  
 `mayBeNull`  
 Opcional.  Especifica se a variável documentado pode ser definido como nulo.  Defina a `true` para indicar que a variável pode ser definido como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementType`  
 Opcional.  Se `type` é `Array`, esse atributo especifica o tipo dos elementos da matriz.  
  
 `elementInteger`  
 Opcional.  Se `type` é `Array` e `elementType` é `Number`, esse atributo especifica se os elementos na matriz são números inteiros.  Defina a `true` para indicar que os elementos na matriz são números inteiros; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementDomElement`  
 Opcional.  Esse atributo é substituído; o atributo de `elementType` tem precedência sobre este atributo.  Se `type` é `Array`, esse atributo especifica se os elementos na matriz são elementos DOM.  Defina a `true` para especificar que os elementos são elementos DOM; se não, defina a `false`.  Se o atributo de `elementType` não está definido e `elementDomElement` é definido como `true`, o IntelliSense trata cada elemento na matriz como `HTMLElement` ao executar a instrução.  
  
 `elementMayBeNull`  
 Opcional.  Se `type` é `Array`, especifica se os elementos na matriz podem ser definidos como nulo.  Defina a `true` para indicar que os elementos na matriz podem ser definidos como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `helpKeyword`  
 Opcional.  A palavra\-chave para F1 ajuda.  
  
 `locid`  
 Opcional.  O identificador para informações de localização sobre a variável.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado na marca de [\< loc \>](../ide/loc-javascript.md) .  
  
 `description`  
 Opcional.  Uma descrição da variável.  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar o elemento de `<var>` .  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)