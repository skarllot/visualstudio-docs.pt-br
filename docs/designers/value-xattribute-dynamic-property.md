---
title: "Valor (propriedade dinâmica de XAttribute) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
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
ms.openlocfilehash: c013001a52e5b894bcbcdaf9a40309505b39140c
ms.lasthandoff: 02/22/2017

---
# <a name="value-xattribute-dynamic-property"></a>Valor (propriedade dinâmica de XAttribute)
Obtém ou define o valor de atributo XML.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 Um <xref:System.String> que contém o valor desse atributo.  
  
## <a name="exceptions"></a>Exceções  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|Ao definir, `value` é `null`.|  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente a <xref:System.Xml.Linq.XAttribute.Value%2A>, propriedade da classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, mas essa propriedade dinâmica também dá suporte a notificações de alteração.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Propriedades dinâmicas da classe XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Attribute](../designers/attribute-xelement-dynamic-property.md)
