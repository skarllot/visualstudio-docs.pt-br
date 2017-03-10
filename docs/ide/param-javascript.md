---
title: "&lt; Param &gt; (JavaScript) | Microsoft Docs"
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
  - "< Param > marca XML JavaScript"
  - "marca XML de param JavaScript"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica informações sobre a documentação para um parâmetro em uma função ou em um método.  
  
## Sintaxe  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### Parâmetros  
 `name`  
 Obrigatório.  O nome do parâmetro.  
  
 `type`  
 Opcional.  O tipo de dados do parâmetro.  O tipo pode ser um dos seguintes:  
  
-   Um idioma ECMAScript na especificação de ECMAScript 5, como `Number` e `Object`.  
  
-   O objeto DOM, como `HTMLElement`, `Window`, e `Document`.  
  
-   Uma função de construtor de JavaScript.  
  
 `integer`  
 Opcional.  Se `type` é `Number`, especifica se o parâmetro é um número inteiro.  Defina a `true` para indicar que o parâmetro é um inteiro; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `domElement`  
 Opcional.  Esse atributo é substituído; o atributo de `type` tem precedência sobre este atributo.  Esse atributo especifica se o parâmetro documentado é um elemento DOM.  Defina a `true` para especificar que o parâmetro é um elemento DOM; se não, defina a `false`.  Se o atributo de `type` não está definido e `domElement` é definido como `true`, o IntelliSense trata o parâmetro documentado como `HTMLElement` ao executar a instrução.  
  
 `mayBeNull`  
 Opcional.  Especifica se o parâmetro documentado pode ser definido como nulo.  Defina a `true` para indicar que o parâmetro pode ser definido como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementType`  
 Opcional.  Se `type` é `Array`, esse atributo especifica o tipo dos elementos da matriz.  
  
 `elementInteger`  
 Opcional.  Se `type` é `Array` e `elementType` é `Number`, esse atributo especifica se os elementos na matriz são números inteiros.  Defina a `true` para indicar que os elementos na matriz são números inteiros; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementDomElement`  
 Opcional.  Esse atributo é substituído; o atributo de `elementType` tem precedência sobre este atributo.  Se `type` é `Array`, esse atributo especifica se os elementos na matriz são elementos DOM.  Defina a `true` para especificar que os elementos são elementos DOM; se não, defina a `false`.  Se o atributo de `elementType` não está definido e `elementDomElement` é definido como `true`, o IntelliSense trata cada elemento na matriz como `HTMLElement` ao executar a instrução.  
  
 `elementMayBeNull`  
 Opcional.  Se `type` é `Array`, especifica se os elementos na matriz podem ser definidos como nulo.  Defina a `true` para indicar que os elementos na matriz podem ser definidos como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `locid`  
 Opcional.  O identificador para informações sobre localização do parâmetro.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado no elemento de [\< loc \>](../ide/loc-javascript.md) .  
  
 `parameterArray`  
 Opcional.  Especifica se o parâmetro documentado pode ser repetido na chamada de função, semelhante a repetir os parâmetros suportados na função de `String.format` .  Defina a `true` para indicar que o parâmetro pode ser repetido; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `optional`  
 Opcional.  Especifica se o parâmetro é opcional documentado na função de chamada.  Defina a `true` para indicar que o parâmetro é opcional; se não, defina a `false`.  
  
 `value`  
 Opcional.  Especifica o código que deve ser avaliado para o uso do IntelliSense em vez de código de função próprio.  Você pode usar este atributo deve fornecer informações de tipo quando o tipo de parâmetro é indefinido.  Por exemplo, você pode usar `value=’1’` para manipular o tipo de parâmetro como um número.  
  
 `description`  
 Opcional.  Uma descrição do parâmetro.  
  
## Comentários  
 O único atributo é necessário `name`.  Todos os outros atributos são opcionais.  
  
 Os elementos usados para fazer anotações funções, como [\< resumo \>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), e [\< retorna \>](../ide/returns-javascript.md), devem ser colocados no corpo da função antes de quaisquer declarações.  
  
 Se houver vários elementos de `<param>` que têm o mesmo nome, um dos elementos de `<param>` é usado e elementos redundantes são ignorados.  O comportamento que determina qual elemento é usado não está definido.  Se `name` se refere a um parâmetro inexistente, o elemento é ignorado.  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar o elemento de `<param>` .  
  
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
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)