---
title: "Evento &#39;&lt; eventname &gt;&#39; n&#227;o pode ser tratado porque ele n&#227;o &#233; acess&#237;vel a partir de &#39;&lt; nome &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30585"
  - "vbc30585"
helpviewer_keywords: 
  - "BC30585"
ms.assetid: fe039f8f-be6f-4b52-86bd-d551c54b85cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Evento &#39;&lt; eventname &gt;&#39; n&#227;o pode ser tratado porque ele n&#227;o &#233; acess&#237;vel a partir de &#39;&lt; nome &gt;&#39;
Você tentou manipular um evento que não está acessível. Por exemplo, se um `Handles` variável for compartilhada, o método de manipulação de eventos também deve ser compartilhado.  
  
 **ID do erro:** BC30585  
  
### Para corrigir este erro  
  
1.  Verifique se o evento está acessível.  
  
## Consulte também  
 [NÃO nos manipuladores de eventos e eventos de compilação:](http://msdn.microsoft.com/pt-br/95074a0d-1cbc-4221-a95a-964185c7f962)