---
title: "Defini&#231;&#227;o de &#39;RaiseEvent&#39; ausente para o evento &#39;&lt; eventname &gt;&#39; | Microsoft Docs"
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
  - "vbc31132"
  - "bc31132"
helpviewer_keywords: 
  - "BC31132"
ms.assetid: 8f3442fd-2ed1-4dbc-83a8-f0860ec022ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Defini&#231;&#227;o de &#39;RaiseEvent&#39; ausente para o evento &#39;&lt; eventname &gt;&#39;
Se um evento é declarado como `Custom`, ele deve fornecer um procedimento para disparar o evento.  
  
 **ID do erro:** BC31132  
  
### Para corrigir este erro  
  
1.  Incluir um `RaiseEvent` declaração entre o `Custom Event` instrução e `End Event` instrução.  
  
2.  Verifique se outros procedimentos dentro da declaração de evento são terminados corretamente.  
  
## Consulte também  
 [Instrução RaiseEvent](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)