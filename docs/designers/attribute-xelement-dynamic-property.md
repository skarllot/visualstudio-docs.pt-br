---
title: "Atributo (Propriedade Dinâmica XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
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
ms.openlocfilehash: f2feac03ad0fba1866a1df759fb6ffcf5a17aff6
ms.lasthandoff: 02/22/2017

---
# <a name="attribute-xelement-dynamic-property"></a>Atributo (propriedade dinâmica de XElement)
Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 Um indicador de tipo `XAttribute Item(String expandedName)`. Esse indexador utiliza o nome expandido do atributo especificado e retorna o <xref:System.Xml.Linq.XAttribute> correspondente ou `null` se não houver nenhum atributo com o nome especificado.  
  
## <a name="remarks"></a>Comentários  
 Essa propriedade é equivalente ao método <xref:System.Xml.Linq.XElement.Attribute%2A> da classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xattribute-dynamic-property.md)
