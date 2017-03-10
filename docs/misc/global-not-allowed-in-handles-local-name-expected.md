---
title: "&#39;Global&#39; n&#227;o permitido em identificadores; nome local esperado | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; n&#227;o permitido em identificadores; nome local esperado
Um `Handles` cláusula deve se referir a um evento local. O `Global` palavra\-chave fornece acesso aos elementos de programação globais.  
  
 **ID do erro:** BC36002  
  
### Para corrigir este erro  
  
-   Alteração de `Handles` cláusula para se referir a uma instância local do evento em vez da instância global.  
  
## Consulte também  
 [Global \- excluir](http://msdn.microsoft.com/pt-br/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)