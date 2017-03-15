---
title: "&lt; Resumo &gt; (JavaScript) | Microsoft Docs"
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
  - "marca XML de resumo JavaScript"
  - "Marca < summary > JavaScript XML"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Resumo &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica uma descrição para uma função ou método.  
  
## Sintaxe  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### Parâmetros  
 `locid`  
 Opcional.  O identificador para informações de localização sobre a função ou método.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado no elemento de [\< loc \>](../ide/loc-javascript.md) .  
  
 `description`  
 Opcional.  Uma descrição da função ou método.  
  
## Comentários  
 Os elementos usados para fazer anotações funções, que incluem [\<summary\>](../ide/summary-javascript.md), [\< param \>](../ide/param-javascript.md), e [\< retorna \>](../ide/returns-javascript.md), devem ser colocados no corpo da função antes de quaisquer declarações.  
  
## Exemplo  
 O código a seguir mostra como usar o elemento de `<summary>` .  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)