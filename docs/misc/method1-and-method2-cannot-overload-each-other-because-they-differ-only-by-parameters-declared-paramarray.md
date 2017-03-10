---
title: "&#39;&lt; method1 &gt;&#39; e &#39;&lt; method2 &gt;&#39; n&#227;o pode sobrecarregar porque diferem somente pelos par&#226;metros declarados &#39;ParamArray&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; e &#39;&lt; method2 &gt;&#39; n&#227;o pode sobrecarregar porque diferem somente pelos par&#226;metros declarados &#39;ParamArray&#39;
Você tentou sobrecarregar dois métodos que diferem entre si somente por um `ParamArray` ou mais parâmetros. O compilador considera um procedimento com um `ParamArray` parâmetro deverá ter um número infinito de sobrecargas diferindo entre si no que é passado para a matriz de parâmetros.  
  
 **ID do erro:** BC30368  
  
### Para corrigir este erro  
  
-   Certifique\-se de que os métodos são diferenciados por mais do que o `ParamArray` parâmetros.  
  
## Consulte também  
 [Considerações sobre procedimentos de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Matrizes de parâmetros](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)