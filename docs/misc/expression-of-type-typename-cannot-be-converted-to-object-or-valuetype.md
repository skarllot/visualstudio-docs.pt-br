---
title: "Express&#227;o do tipo &#39;&lt; typename &gt;&#39; n&#227;o pode ser convertido em &#39;Object&#39; ou &#39;ValueType&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o do tipo &#39;&lt; typename &gt;&#39; n&#227;o pode ser convertido em &#39;Object&#39; ou &#39;ValueType&#39;
Uma expressão é avaliada como um tipo que não pode ser convertido pelo common language runtime \(CLR\).  
  
 *Conversão boxing* refere\-se ao processamento necessário para converter um tipo para `Object` ou, ocasionalmente, para <xref:System.ValueType>. O common language runtime não é possível caixa certos tipos de, por exemplo <xref:System.ArgIterator> e <xref:System.TypedReference>.  
  
 Se você não usou `CType` ou `CObj` na instrução que contém essa expressão [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tentou uma conversão implícita que causa esse erro.  
  
 **ID do erro:** BC31394  
  
### Para corrigir este erro  
  
1.  Localize a expressão que é avaliada como o tipo citado.  
  
2.  Localize a parte da sua declaração que tenta caixa o tipo citado.  
  
3.  Reescreva a instrução para evitar a conversão boxing.  
  
## Consulte também  
 [Conversões implícitas e explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)