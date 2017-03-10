---
title: "Criar coment&#225;rios JSDoc para JavaScript IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Criar coment&#225;rios JSDoc para JavaScript IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense no Visual Studio exibe informações que você adiciona um script usando comentários JSDoc padrão.  Você pode usar comentários JSDoc para fornecer informações sobre elementos de código, como variáveis, funções e campos.  
  
## Marcas de comentário JSDoc  
 As seguintes marcas de comentário JSDoc padrão são usadas pelo IntelliSense para exibir informações sobre seu código.  
  
|Marca JSDoc|Sintaxe|Observações|  
|-----------------|-------------|-----------------|  
|@ preterido|@ preterido *Descrição*|Especifica um método ou função preterida.|  
|@description|@description *Descrição*|Especifica a descrição para uma função ou método.|  
|@param|@param {*tipo*} *parameterName**Descrição*|Especifica informações de um parâmetro em uma função ou método.<br /><br /> O typeScript também oferece suporte a @paramTag.|  
|@property|@property {*tipo*} *propertyName*|Especifica as informações, incluindo uma descrição, para um campo ou um membro que é definido em um objeto.|  
|@returns|@returns {*tipo*}|Especifica um valor de retorno.<br /><br /> Para o TypeScript, use @returnType em vez de @returns.|  
|@summary|@summary *Descrição*|Especifica a descrição de uma função ou um método \(o mesmo que @description\).|  
|@type|@type {*tipo*}|Especifica o tipo de uma constante ou uma variável.|  
|@typedef|@typedef {*tipo*} *customTypeName*|Especifica um tipo personalizado.|  
  
### Exemplos  
 O exemplo a seguir mostra o uso do @description, @param e @return JSDoc marcas para uma função chamada `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 No exemplo anterior, o IntelliSense mostra a descrição, parâmetro e retornar informações quando você digita o parêntese de abertura para `getArea`.  
  
 ![IntelliSense information for a function](../ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 O exemplo a seguir mostra como usar a marca @typedef com a marca @property.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 O exemplo a seguir mostra o uso do @type JSDoc marcas.  Conforme mostrado neste exemplo, o único asteriscos \(\*\) que execute o par inicial de asterisco \(\*\) não são necessários.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 O exemplo a seguir mostra como usar o @ preterido JSDoc marca.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```