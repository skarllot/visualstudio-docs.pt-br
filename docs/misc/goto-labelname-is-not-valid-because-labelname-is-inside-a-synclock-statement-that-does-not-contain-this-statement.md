---
title: "&#39;GoTo &lt; labelname &gt;&#39; n&#227;o &#233; v&#225;lido porque &#39;&lt; labelname &gt;&#39; est&#225; dentro de uma instru&#231;&#227;o &#39;SyncLock&#39; que n&#227;o cont&#233;m essa declara&#231;&#227;o | Microsoft Docs"
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
  - "bc30755"
  - "vbc30755"
helpviewer_keywords: 
  - "BC30755"
ms.assetid: 95fb48c1-4982-45fc-81f0-f30cf0df173f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt; labelname &gt;&#39; n&#227;o &#233; v&#225;lido porque &#39;&lt; labelname &gt;&#39; est&#225; dentro de uma instru&#231;&#227;o &#39;SyncLock&#39; que n&#227;o cont&#233;m essa declara&#231;&#227;o
Você não pode ramificar em um `SyncLock` bloco.  
  
 **ID do erro:** BC30755  
  
### Para corrigir este erro  
  
-   Reestruturar o código para que o rótulo preceda o `SyncLock` bloco.  
  
## Consulte também  
 [Instrução SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)