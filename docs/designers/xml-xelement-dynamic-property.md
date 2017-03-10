---
title: "Xml (XElement Dynamic Property) | Microsoft Docs"
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
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtém o conteúdo sem formatação XML do elemento.  
  
## Sintaxe  
  
```  
elem.Xml  
```  
  
## Valor da propriedade\/valor de retorno  
 <xref:System.String> que representa o conteúdo sem formatação XML do elemento.  
  
## Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.  
  
## Consulte também  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xelement-dynamic-property.md)