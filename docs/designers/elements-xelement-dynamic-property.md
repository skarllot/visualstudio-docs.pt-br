---
title: "Elements (propriedade dinâmica de XElement)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
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
ms.openlocfilehash: 24dc395f229ae79696df926630c7e72b5ad1672d
ms.lasthandoff: 02/22/2017

---
# <a name="elements-xelement-dynamic-property"></a>Elementos (propriedade dinâmica de XElement)
Obtém um indexador usado para recuperar elementos filho do elemento atual que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Valor de propriedade/Valor de retorno  
 Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse indexador utiliza o nome expandido de elementos filhos desejados e retorna os elementos filhos correspondentes em uma coleção <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> da classe <xref:System.Xml.Linq.XContainer>.  
  
 Os elementos na coleção retornada estão na ordem de documento-fonte XML.  
  
 Esta propriedade usa a execução adiada.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elemento](../designers/element-xelement-dynamic-property.md)   
 [Descendentes](../designers/descendants-xelement-dynamic-property.md)
