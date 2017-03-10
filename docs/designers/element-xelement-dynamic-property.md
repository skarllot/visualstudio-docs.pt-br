---
title: "Element (XElement Dynamic Property) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Element (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtém um indexador usado para recuperar a instância do elemento filho que corresponde ao nome especificado expandido.  
  
## Sintaxe  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## Valor da propriedade\/valor de retorno  
 Um indicador de tipo `XElement Item(String expandedName)`.  Esse marcador aceita um parâmetro expandido de nome e retorna <xref:System.Xml.Linq.XElement>correspondente, ou `null` se não houver nenhum elemento com o nome especificado.  
  
## Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Element%2A> da classe de <xref:System.Xml.Linq.XContainer?displayProperty=fullName> .  
  
## Consulte também  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)