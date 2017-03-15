---
title: "O par&#226;metro lambda &#39;&lt; parameter &gt;&#39; oculta uma vari&#225;vel em um bloco delimitador, uma vari&#225;vel de intervalo definida anteriormente ou uma vari&#225;vel declarada implicitamente em uma express&#227;o de consulta. | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro lambda &#39;&lt; parameter &gt;&#39; oculta uma vari&#225;vel em um bloco delimitador, uma vari&#225;vel de intervalo definida anteriormente ou uma vari&#225;vel declarada implicitamente em uma express&#227;o de consulta.
Uma variável em uma expressão lambda tem o mesmo nome que uma variável anteriormente definida dentro do mesmo escopo. Isso pode ser uma variável em um bloco delimitador de código para uma variável que é declarada implicitamente para uma consulta LINQ, uma variável de intervalo definida anteriormente em uma consulta LINQ ou uma expressão lambda aninhada.  
  
 **ID do erro:** BC36641  
  
### Para corrigir este erro  
  
-   Certifique\-se de que todas as variáveis na expressão lambda tenham nomes exclusivos que não duplicam nomes de variável existentes no mesmo escopo.  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)