---
title: "LINQ to XML Dynamic Properties | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LINQ to XML Dynamic Properties
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta seção fornece informações de referência sobre as propriedades dinâmicas em LINQ to XML.  Especificamente, essas propriedades são expostos por classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que estão no espaço de <xref:System.Xml.Linq> .  
  
 Conforme explicado no tópico [Visão geral de associação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada uma das propriedades dinâmicas é equivalente a uma propriedade pública ou método padrão na mesma classe.  Esses membros padrão devem ser usados para a maioria das finalidades; as propriedades dinâmicas são fornecidas especificamente para cenários de associação de dados LINQ to XML.  Para obter mais informações sobre membros padrão dessas classes, consulte os tópicos de referência de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> .  
  
 Em relação a seus valores resolvidos, as propriedades dinâmicas nesta seção se enquadram em duas categorias:  
  
-   O simples, como as propriedades de `Value` classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que são consideradas como um único valor.  
  
-   Valores indexados, como as propriedades de [Elementos](../designers/elements-xelement-dynamic-property.md) e de [Descendentes](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que determinam em um tipo de indicador.  Para que os tipos do indexador são resolvidos com o valor desejado ou à coleção, um parâmetro expandido do nome deve ser\-lhes passado.  
  
 Todas as propriedades dinâmicas que retornam um valor indexado de uso de <xref:System.Collections.Generic.IEnumerable%601> de tipo deffered a execução.  Para obter mais informações sobre a execução adiada, consulte [Introdução a consultas LINQ \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Nesta seção  
  
|Tópico|Descrição|  
|------------|---------------|  
|[XAttribute Class Dynamic Properties](../designers/xattribute-class-dynamic-properties.md)|Fornece detalhes sobre as propriedades dinâmicas expostos pela classe de <xref:System.Xml.Linq.XAttribute> .|  
|[XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)|Fornece detalhes sobre as propriedades dinâmicas expostos pela classe de <xref:System.Xml.Linq.XElement> .|  
  
## Referência  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## Consulte também  
 [WPF Data Binding with LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [WPF Data Binding with LINQ to XML Overview](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introdução a consultas LINQ \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)