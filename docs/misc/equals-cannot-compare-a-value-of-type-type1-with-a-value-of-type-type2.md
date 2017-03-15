---
title: "&#39;Equals&#39; n&#227;o pode comparar um valor do tipo &lt; type1 &gt; com um valor do tipo &lt; type2 &gt; | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; n&#227;o pode comparar um valor do tipo &lt; type1 &gt; com um valor do tipo &lt; type2 &gt;
Um `Equals` operador em uma `Join` ou `Group Join` cláusula tentou comparar um tipo de dados para outro de forma que não está definida. Um exemplo disso é uma comparação de uma `Boolean` valor para um `Date` tipo.  
  
 **ID do erro:** BC36621  
  
### Para corrigir este erro  
  
-   Verifique se os valores em cada lado do `Equals` operador pode ser convertido em um tipo de dados comum. Algumas opções para realizar isso são:  
  
    -   Use o `CType` função para converter um ou mais dos valores a um tipo específico.  
  
    -   Use o <xref:System.Convert> métodos de classe ou de conversão para converter um ou mais dos valores em um tipo comum e imutável.  
  
    -   Converter os valores em cadeias de caracteres usando o `ToString` método.  
  
## Consulte também  
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Cláusula Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Cláusula Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)