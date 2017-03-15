---
title: "Marca de coment&#225;rio XML &#39;returns&#39; n&#227;o &#233; permitida em um elemento de linguagem &#39;declare sub&#39; | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Marca de coment&#225;rio XML &#39;returns&#39; n&#227;o &#233; permitida em um elemento de linguagem &#39;declare sub&#39;
Marca de comentário XML 'returns' não é permitida em um elemento de linguagem 'declare sub'. O comentário XML será ignorado.  
  
 Um comentário XML para uma `Declare Sub` declaração não pode conter um `<`retorna`>` marca.  
  
 **ID do erro:** BC42315  
  
### Para corrigir este erro  
  
-   Remover o suporte `<`retorna`>` marca.  
  
## Consulte também  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [Marcas de comentário XML](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documentando o código com XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Instrução Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)