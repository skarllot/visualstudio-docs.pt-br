---
title: "&lt; Preterido &gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Preterido &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica uma função ou um método substituído.  
  
## Sintaxe  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### Parâmetros  
 `type`  
 Opcional.  Especifica se a função ou o método serão removidos em uma versão futura, ou se a função ou o método tiverem sido removidos já e que seu uso pode resultar em um erro.  Defina a `deprecate` para especificar que a função ou o método serão removidos em uma versão futura.  Defina a `remove` para especificar que a função ou o método tiverem sido removidos.  
  
 `locid`  
 Opcional.  O identificador para informações de localização sobre a função ou método.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado no elemento de [\< loc \>](../ide/loc-javascript.md) .  
  
 `description`  
 Opcional.  Uma descrição da função ou método que está sendo substituído.  
  
## Comentários  
 Os elementos usados para fazer anotações funções, que incluem `<deprecated>`, devem ser colocados no corpo da função antes de quaisquer declarações.  Quando você marca uma função como substituída, recomendamos que você substitua o elemento de [\< resumo \>](../ide/summary-javascript.md) com o elemento de `<deprecated>` .  
  
## Exemplo  
 O código a seguir mostra como usar o elemento de `<deprecated>` .  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)