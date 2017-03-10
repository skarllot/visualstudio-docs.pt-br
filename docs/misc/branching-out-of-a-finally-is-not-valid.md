---
title: "Ramifica&#231;&#227;o fora de um &#39;Finally&#39; n&#227;o &#233; v&#225;lido | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ramifica&#231;&#227;o fora de um &#39;Finally&#39; n&#227;o &#233; v&#225;lido
Um `GoTo` instrução dentro de um `Finally` Bloquear ramificações fora do bloco. Não é válido ramificar dentro ou fora de um `Catch` ou `Finally` bloco.  
  
 **ID do erro:** BC30101  
  
### Para corrigir este erro  
  
-   Remover o `GoTo` instrução e considere implementar a lógica do programa com estruturas de controle de decisão ou loop.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Instrução GoTo](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Fluxo de controle](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)