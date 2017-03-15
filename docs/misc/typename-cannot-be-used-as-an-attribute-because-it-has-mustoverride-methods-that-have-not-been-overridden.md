---
title: "&#39;&lt; typename &gt;&#39; n&#227;o pode ser usado como um atributo porque tem m&#233;todos &#39;MustOverride&#39; que n&#227;o foram substitu&#237;dos | Microsoft Docs"
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
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; n&#227;o pode ser usado como um atributo porque tem m&#233;todos &#39;MustOverride&#39; que n&#227;o foram substitu&#237;dos
Classes com `MustOverride` métodos não podem ser usados como atributos.  
  
 `MustOverride` membros de classes de atributos só podem ser usados de classes derivadas que substituem esses membros.  
  
 **ID do erro:** BC31507  
  
### Para corrigir este erro  
  
1.  Remover o `MustOverride` modificador de membros de classe de atributo.  
  
2.  Implementar `MustOverride` membros em uma classe derivada e use essa classe como um atributo.  
  
## Consulte também  
 <xref:System.AttributeUsageAttribute>   
 [NÃO está em compilação: Atributos personalizados no Visual Basic](http://msdn.microsoft.com/pt-br/d72d8a5c-8f64-4614-b15b-cad66845d047)