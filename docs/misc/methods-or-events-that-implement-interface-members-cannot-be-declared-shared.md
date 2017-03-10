---
title: "M&#233;todos ou eventos que implementam membros de interface n&#227;o podem ser declarados &#39;Shared&#39; | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos ou eventos que implementam membros de interface n&#227;o podem ser declarados &#39;Shared&#39;
Você tentou declarar como `Shared` um método ou evento que implementa um membro de interface. Métodos e eventos sendo implementados em uma classe não podem ser designados `Shared` ou `Private`, exceto em uma classe não\-herdável.  
  
 **ID do erro:** BC30505  
  
### Para corrigir este erro  
  
-   Remover o `Shared` palavra\-chave.  
  
## Consulte também  
 [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)