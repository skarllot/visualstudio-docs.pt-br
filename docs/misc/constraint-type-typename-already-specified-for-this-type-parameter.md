---
title: "Tipo de restri&#231;&#227;o &#39;&lt; typename &gt;&#39; j&#225; especificado para este par&#226;metro de tipo | Microsoft Docs"
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
  - "BC32071"
  - "vbc32071"
helpviewer_keywords: 
  - "BC32071"
ms.assetid: 6b0e85e9-3ac8-4181-97de-ca690b95a63c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de restri&#231;&#227;o &#39;&lt; typename &gt;&#39; j&#225; especificado para este par&#226;metro de tipo
Uma lista de restrições inclui uma restrição de classe ou interface mais de uma vez.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Você pode especificar os seguintes requisitos em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
 Um tipo não pode implementar ou herdar de mesmo tipo mais de uma vez, e você não pode especificar um tipo mais de uma vez na mesma lista de restrição.  
  
 **ID do erro:** BC32071  
  
### Para corrigir este erro  
  
-   Remova quaisquer especificações supérfluas de mesma classe ou interface. Ele deve aparecer apenas uma vez na lista de restrição.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)