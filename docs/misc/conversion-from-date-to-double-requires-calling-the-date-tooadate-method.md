---
title: "Convers&#227;o de &#39;Date&#39; em &#39;Double&#39; requer chamar o m&#233;todo &#39;ToOADate&#39; | Microsoft Docs"
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
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#227;o de &#39;Date&#39; em &#39;Double&#39; requer chamar o m&#233;todo &#39;ToOADate&#39;
Você tentou lançar um `Date` valor para um `Double` valor, que não pode ser feito sem usar o <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> método.  
  
 **ID do erro:** BC30532  
  
### Para corrigir este erro  
  
-   Use o <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> método para converter o valor.  
  
## Consulte também  
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)