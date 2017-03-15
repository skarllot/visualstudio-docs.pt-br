---
title: "&lt; Retorna &gt; (JavaScript) | Microsoft Docs"
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
  - "retorna a marca XML JavaScript"
  - "Marca < returns > JavaScript XML"
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Retorna &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica informações sobre a documentação para o resultado de uma chamada de função ou método.  
  
## Sintaxe  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### Parâmetros  
 `type`  
 Opcional.  O tipo de dados do valor de retorno.  O tipo pode ser um dos seguintes:  
  
-   Um idioma ECMAScript na especificação de ECMAScript 5, como `Number` e `Object`.  
  
-   O objeto DOM, como `HTMLElement`, `Window`, e `Document`.  
  
-   Uma função de construtor de JavaScript.  
  
 `integer`  
 Opcional.  Se `type` é `Number`, especifica se o valor de retorno é um número inteiro.  Defina a `true` para indicar que o valor de retorno é um inteiro; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `domElement`  
 Opcional.  Esse atributo é substituído; o atributo de `type` tem precedência sobre este atributo.  Esse atributo especifica se o valor de retorno documentado é um elemento DOM.  Defina a `true` para especificar que o valor de retorno é um elemento DOM; se não, defina a `false`.  Se o atributo de `type` não está definido e `domElement` é definido como `true`, o IntelliSense trata o valor de retorno documentado como `HTMLElement` ao executar a instrução.  
  
 `mayBeNull`  
 Opcional.  Especifica se o valor de retorno documentado pode ser definido como nulo.  Defina a `true` para indicar que o valor de retorno pode ser definido como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementType`  
 Opcional.  Se `type` é `Array`, esse atributo especifica o tipo dos elementos da matriz.  
  
 `elementInteger`  
 Opcional.  Se `type` é `Array` e `elementType` é `Number`, esse atributo especifica se os elementos na matriz são números inteiros.  Defina a `true` para indicar que os elementos na matriz são números inteiros; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementDomElement`  
 Opcional.  Esse atributo é substituído; o atributo de `elementType` tem precedência sobre este atributo.  Se `type` é `Array`, esse atributo especifica se os elementos na matriz são elementos DOM.  Defina a `true` para especificar que os elementos são elementos DOM; se não, defina a `false`.  Se o atributo de `elementType` não está definido e `elementDomElement` é definido como `true`, o IntelliSense trata cada elemento na matriz como `HTMLElement` ao executar a instrução.  
  
 `elementMayBeNull`  
 Opcional.  Se `type` é `Array`, especifica se os elementos na matriz podem ser definidos como nulo.  Defina a `true` para indicar que os elementos na matriz podem ser definidos como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `locid`  
 Opcional.  O identificador para informações de localização sobre o valor de retorno.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado na marca de [\< loc \>](../ide/loc-javascript.md) .  
  
 `value`  
 Opcional.  Especifica o código que deve ser avaliado para o uso do IntelliSense em vez de código de função próprio.  Por exemplo, você pode usar esse atributo para fornecer o IntelliSense para callbacks assíncronas, como `Promise`.  Usar o atributo de `value` com o elemento de `<returns>` pode melhorar o desempenho do IntelliSense ignorando a execução longa de código.  
  
 `description`  
 Opcional.  Uma descrição de valor de retorno.  
  
## Comentários  
 O elemento de `<returns>` deve ser colocado no corpo da função antes de quaisquer declarações.  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar o elemento de `<returns>` .  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)