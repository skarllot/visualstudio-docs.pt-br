---
title: "&#39;&lt; nome do membro &gt;&#39; existe em v&#225;rias interfaces base | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; nome do membro &gt;&#39; existe em v&#225;rias interfaces base
'\< nome do membro \>' existe em várias interfaces base. Use o nome da interface que declara '\< nome do membro \>' na cláusula 'Implements' em vez do nome da interface derivada.  
  
 Esta interface herda os membros com o mesmo nome de várias interfaces, criando ambigüidade.  
  
 **ID do erro:** BC31040  
  
### Para corrigir este erro  
  
-   Use o nome da interface definição no `Implements` cláusulas em vez do nome da interface derivada.  
  
## Consulte também  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)