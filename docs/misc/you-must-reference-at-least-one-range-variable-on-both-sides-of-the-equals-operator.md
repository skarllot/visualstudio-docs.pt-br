---
title: "Voc&#234; deve referenciar pelo menos uma vari&#225;vel range em ambos os lados do operador &#39;Equals&#39; | Microsoft Docs"
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
  - "vbc36622"
  - "bc36622"
helpviewer_keywords: 
  - "BC36622"
ms.assetid: 8d301227-131d-4977-b3ff-1fc4e427f8fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Voc&#234; deve referenciar pelo menos uma vari&#225;vel range em ambos os lados do operador &#39;Equals&#39;
Você deve referenciar pelo menos uma variável range em ambos os lados do operador 'Equals'. Variáveis de intervalo \< variáveis \> devem aparecer em um lado do operador 'Equals' e as variáveis de intervalo \< variáveis \> devem aparecer em outro.  
  
 Variáveis range identificadas por coleções a serem unidas em uma consulta LINQ deve estar em lados opostos do `Equals` operador, dependendo da coleção são identificados. Isto é, variáveis range identificadas por uma das coleções que estão sendo unidas deve ser no lado oposto do `Equals` operador das variáveis range para outra coleção a ser ligada. Variáveis Range de coleções separadas não podem ser misturadas no mesmo lado do `Equals` operador.  
  
 Pelo menos uma variável de cada coleção a ser ligada deve ser referenciada em cada lado do `Equals` operador.  
  
 **ID do erro:** BC36622  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Cláusula Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Cláusula Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Cláusula From](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Cláusula Select](/dotnet/visual-basic/language-reference/queries/select-clause)