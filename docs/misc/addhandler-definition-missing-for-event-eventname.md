---
title: "Defini&#231;&#227;o de &#39;AddHandler&#39; ausente para o evento &#39;&lt; eventname &gt;&#39; | Microsoft Docs"
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
  - "bc31130"
  - "vbc31130"
helpviewer_keywords: 
  - "BC31130"
ms.assetid: cf6c7fd6-ce2e-4916-b427-2a4a63e7279d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Defini&#231;&#227;o de &#39;AddHandler&#39; ausente para o evento &#39;&lt; eventname &gt;&#39;
Se um evento é declarado como `Custom`, ele deve fornecer um procedimento para adicionar um manipulador de eventos.  
  
 **ID do erro:** BC31130  
  
### Para corrigir este erro  
  
1.  Incluir um `AddHandler` declaração entre o `Custom Event` instrução e `End Event` instrução.  
  
2.  Verifique se que outros procedimentos no final de declaração de evento corretamente.  
  
## Consulte também  
 [Instrução AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)