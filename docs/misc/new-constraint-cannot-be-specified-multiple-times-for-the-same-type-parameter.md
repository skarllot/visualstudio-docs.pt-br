---
title: "A restri&#231;&#227;o &#39;New&#39; n&#227;o pode ser especificada v&#225;rias vezes para o mesmo par&#226;metro de tipo | Microsoft Docs"
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
  - "vbc32081"
  - "BC32081"
helpviewer_keywords: 
  - "BC32081"
ms.assetid: afcb30da-3973-4452-9cf3-c027f9866589
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A restri&#231;&#227;o &#39;New&#39; n&#227;o pode ser especificada v&#225;rias vezes para o mesmo par&#226;metro de tipo
Uma lista de restrição inclui o [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator) restrição mais de uma vez.  
  
 Uma lista de restrição em um parâmetro de tipo pode especificar que o argumento passado para esse parâmetro do tipo deve expor um construtor sem parâmetros que o código de criação pode acessar. Um tipo não pode ter mais de um construtor sem parâmetros, e você não pode especificar esse requisito mais de uma vez.  
  
 **ID do erro:** BC32081  
  
### Para corrigir este erro  
  
-   Remove qualquer redundante `New` palavras\-chave. Você deve ter apenas um na lista de restrição.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)