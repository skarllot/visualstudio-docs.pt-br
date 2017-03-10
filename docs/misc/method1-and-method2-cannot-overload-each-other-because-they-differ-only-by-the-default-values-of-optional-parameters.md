---
title: "&#39;&lt; method1 &gt;&#39; e &#39;&lt; method2 &gt;&#39; n&#227;o podem sobrecarregar um ao outro porque diferem somente pelos valores padr&#227;o de par&#226;metros opcionais | Microsoft Docs"
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
  - "vbc30305"
  - "bc30305"
helpviewer_keywords: 
  - "BC30305"
ms.assetid: f07f925e-9f95-4885-bdba-eaba2d0483d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; e &#39;&lt; method2 &gt;&#39; n&#227;o podem sobrecarregar um ao outro porque diferem somente pelos valores padr&#227;o de par&#226;metros opcionais
Você tentou sobrecarregar um método com outro método que difere do primeiro somente em seus parâmetros opcionais. Um método com um parâmetro opcional é equivalente a dois métodos sobrecarregados, um com o parâmetro opcional e outro sem ele. Portanto, você não pode sobrecarregar um método com uma lista de argumentos correspondentes a um deles.  
  
 **ID do erro:** BC30305  
  
### Para corrigir este erro  
  
-   Certifique\-se de que os métodos são diferenciados por mais do que apenas os parâmetros opcionais.  
  
## Consulte também  
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerações sobre procedimentos de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)