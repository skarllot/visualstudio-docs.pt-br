---
title: "&#39; Handles&#39; em classes devem especificar uma vari&#225;vel &#39;WithEvents&#39;, &#39;MyBase&#39;, &#39;MyClass&#39; ou &#39;Me&#39; qualificada com um &#250;nico identificador | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39; Handles&#39; em classes devem especificar uma vari&#225;vel &#39;WithEvents&#39;, &#39;MyBase&#39;, &#39;MyClass&#39; ou &#39;Me&#39; qualificada com um &#250;nico identificador
Para especificar um manipulador de eventos `Handles` instruções devem especificar uma variável de objeto declarada com a `WithEvents` palavra\-chave ou um membro qualificados com o `MyBase` palavra\-chave.  
  
 **ID do erro:** BC31412  
  
### Para corrigir este erro  
  
1.  Use o `WithEvents` modificador para declarar as variáveis a serem usados com o `Handles` instrução.  
  
2.  Especifique o nome de um evento para a classe atual na classe base.  
  
## Consulte também  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)