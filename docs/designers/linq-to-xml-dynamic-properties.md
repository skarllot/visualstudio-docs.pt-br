---
title: "Propriedades dinâmicas de LINQ to XML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a83c203c4e9217e28bf650e675b293675c65a14f
ms.lasthandoff: 02/22/2017

---
# <a name="linq-to-xml-dynamic-properties"></a>Propriedades dinâmicas LINQ to XML
Esta seção fornece informações de referência sobre as propriedades dinâmicas em LINQ to XML. Especificamente, essas propriedades são expostas pelas classes <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, que estão no namespace <xref:System.Xml.Linq>.  
  
 Conforme explicado no tópico [Visão geral de vinculação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada uma das propriedades dinâmicas é equivalente a uma propriedade pública ou método padrão na mesma classe. Esses membros padrão devem ser usados para a maioria das finalidades; as propriedades dinâmicas são fornecidas especificamente para cenários de associação de dados LINQ to XML. Para obter mais informações sobre membros padrão dessas classes, consulte os tópicos de referência <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>.  
  
 Em relação a seus valores resolvidos, as propriedades dinâmicas nesta seção se enquadram em duas categorias:  
  
-   As simples, como as propriedades `Value` nas classes <xref:System.Xml.Linq.XAttribute> e <xref:System.Xml.Linq.XElement>, o que resolve para um valor único.  
  
-   Valores indexados, como as propriedades [Elementos](../designers/elements-xelement-dynamic-property.md) e [Descendentes](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que resolvem em um tipo de indexador. Para que os tipos do indexador são resolvidos com o valor desejado ou à coleção, um parâmetro expandido do nome deve ser-lhes passado.  
  
 Todas as propriedades dinâmicas que retornam um valor indexado de tipo <xref:System.Collections.Generic.IEnumerable%601> usam a execução adiada. Para obter mais informações sobre a execução adiada, consulte [Introdução a Consultas de LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Propriedades dinâmicas da classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Fornece detalhes sobre as propriedades dinâmicas expostas pela classe <xref:System.Xml.Linq.XAttribute>.|  
|[Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)|Fornece detalhes sobre as propriedades dinâmicas expostas pela classe <xref:System.Xml.Linq.XElement>.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 [Vinculação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Visão geral da vinculação de dados do WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introdução a consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
