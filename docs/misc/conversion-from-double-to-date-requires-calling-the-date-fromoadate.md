---
title: "Convers&#227;o de &#39;Double&#39; em &#39;Date&#39; requer a chamada &#39;FromOADate&#39; | Microsoft Docs"
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
  - "vbc30533"
  - "bc30533"
helpviewer_keywords: 
  - "BC30533"
ms.assetid: afcfd115-4614-4b0b-ad09-76af8dba2ed5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#227;o de &#39;Double&#39; em &#39;Date&#39; requer a chamada &#39;FromOADate&#39;
Você tentou lançar um `Date` valor para um `Double` valor, que não pode ser feito sem usar o <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> método.  
  
 **ID do erro:** BC30533  
  
### Para corrigir este erro  
  
-   Use o <xref:System.DateTime.FromOADate%2A> método para converter o valor.  
  
## Consulte também  
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)