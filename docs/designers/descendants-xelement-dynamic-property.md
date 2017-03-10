---
title: "Descendants (propriedade dinâmica de XElement)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 78a9401593e900969c27dcd223a2510ea2ffd24f
ms.lasthandoff: 02/22/2017

---
# <a name="descendants-xelement-dynamic-property"></a>Descendentes (propriedade dinâmica de XElement)
Obtém um indexador usado para recuperar todos os elementos descendentes do elemento atual que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse indexador utiliza o nome expandido de elementos descendentes desejados e retorna os elementos filhos correspondentes em uma coleção <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> da classe <xref:System.Xml.Linq.XContainer>.  
  
 Os elementos na coleção retornada estão na ordem de documento-fonte XML.  
  
 Esta propriedade usa a execução adiada.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementos](../designers/elements-xelement-dynamic-property.md)
