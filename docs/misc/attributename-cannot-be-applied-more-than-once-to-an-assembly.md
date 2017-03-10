---
title: "&#39;&lt; attributename &gt;&#39; n&#227;o pode ser aplicado mais de uma vez a um assembly | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; attributename &gt;&#39; n&#227;o pode ser aplicado mais de uma vez a um assembly
O atributo especificado só pode ser aplicado uma vez a um atributo.  
  
 **ID do erro:** BC31521  
  
### Para corrigir este erro  
  
1.  Remova os aplicativos supérfluos deste atributo.  
  
2.  Se você estiver usando um atributo personalizado que você desenvolveu, modificar `AttributeUsageAttribute` e defina o `AllowMultiple` propriedade `True`.  
  
## Consulte também  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>