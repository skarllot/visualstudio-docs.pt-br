---
title: "&#39;&lt; typename &gt;&#39; n&#227;o pode sombrear um m&#233;todo &#39;MustOverride&#39; implicitamente declarado para a propriedade &#39;&lt; propertyname &gt;&#39; &lt; tipo &gt; &#39;&lt; typename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31416"
  - "vbc31416"
helpviewer_keywords: 
  - "BC31416"
ms.assetid: a52aee3c-a19e-412d-bb91-ef1b79e8675f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; n&#227;o pode sombrear um m&#233;todo &#39;MustOverride&#39; implicitamente declarado para a propriedade &#39;&lt; propertyname &gt;&#39; &lt; tipo &gt; &#39;&lt; typename &gt;&#39;
O nome do método especificado está em conflito com um `MustOverride` método implicitamente gerado por uma propriedade na classe base. Por exemplo, se você declarar uma propriedade chamada `Prop1`, o compilador gera os procedimentos implícitos `get_Prop1` e `set_Prop1`.  
  
 **ID do erro:** BC31416  
  
### Para corrigir este erro  
  
1.  Dê ao método um nome exclusivo.  
  
2.  Remover o `MustOverride` modificador da propriedade na classe base.  
  
## Consulte também  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)