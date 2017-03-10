---
title: "Attribute (XElement Dynamic Property) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Attribute (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.  
  
## Sintaxe  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## Valor da propriedade\/valor de retorno  
 Um indicador de tipo `XAttribute Item(String expandedName)`.  Esse marcador utiliza o nome do atributo especificado e retorna <xref:System.Xml.Linq.XAttribute>correspondente, ou `null` se não houver nenhum atributo com o nome especificado.  
  
## Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement?displayProperty=fullName> .  
  
## Consulte também  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xattribute-dynamic-property.md)