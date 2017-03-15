---
title: "Esperado um de &#39;Dim&#39;, &#39;Const&#39;, &#39;Public&#39;, &#39;Private&#39;, &#39;Protected&#39;, &#39;Friend&#39;, &#39;Shadows&#39;, &#39;ReadOnly&#39; ou &#39;Shared&#39; | Microsoft Docs"
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
  - "bc30195"
  - "vbc30195"
helpviewer_keywords: 
  - "BC30195"
ms.assetid: 95684eaa-5aa2-4ae4-9a73-5f97c491e02c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esperado um de &#39;Dim&#39;, &#39;Const&#39;, &#39;Public&#39;, &#39;Private&#39;, &#39;Protected&#39;, &#39;Friend&#39;, &#39;Shadows&#39;, &#39;ReadOnly&#39; ou &#39;Shared&#39;
Uma instrução de declaração não tem uma palavra\-chave de declaração. Uma possível causa é que uma declaração de atributo chama um método.  
  
 **ID do erro:** BC30195  
  
### Para corrigir este erro  
  
1.  Verifique se um método é declarado dentro de uma declaração de atributo.  
  
2.  Inicie a instrução com a palavra\-chave de declaração adequada.  
  
## Consulte também  
 [Elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/index)   
 [Matrizes não podem ser declaradas com 'New'](../misc/arrays-cannot-be-declared-with-new.md)