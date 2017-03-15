---
title: "O operando &#39;TryCast&#39; deve ser tipo de refer&#234;ncia, mas &#39;&lt; typename &gt;&#39; &#233; um tipo de valor | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O operando &#39;TryCast&#39; deve ser tipo de refer&#234;ncia, mas &#39;&lt; typename &gt;&#39; &#233; um tipo de valor
O `TryCast` operador é usado com um tipo de valor para pelo menos um dos argumentos.  
  
 `TryCast` testes de uma relação de herança ou implementação entre os dois argumentos. Portanto, ele permite apenas tipos de referência para os argumentos. Para obter mais informações, consulte [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types).  
  
 **ID do erro:** BC30792  
  
### Para corrigir este erro  
  
-   Use `DirectCast` ou `CType` para realizar a conversão. Os dois permitem tipos de valor.  
  
## Consulte também  
 [Operador TryCast](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Operador DirectCast](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)