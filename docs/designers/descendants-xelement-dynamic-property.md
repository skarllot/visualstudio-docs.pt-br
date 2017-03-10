---
title: "Descendants (XElement Dynamic Property) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Descendants (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtém um indexador usado para recuperar todos os elementos descendentes do elemento atual que corresponde ao nome especificado expandido.  
  
## Sintaxe  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## Valor da propriedade\/valor de retorno  
 Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`.  Esse marcador utiliza o nome expandido de elementos especificados descendente e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .  
  
## Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .  
  
 Os elementos na coleção retornada estão na ordem de documento\-fonte XML.  
  
 Esta propriedade usa a execução adiada.  
  
## Consulte também  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)