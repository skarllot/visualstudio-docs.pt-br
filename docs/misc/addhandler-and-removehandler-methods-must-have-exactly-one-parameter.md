---
title: "M&#233;todos &#39;AddHandler&#39; e &#39;RemoveHandler&#39; devem ter exatamente um par&#226;metro | Microsoft Docs"
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
  - "vbc31133"
  - "bc31133"
helpviewer_keywords: 
  - "BC31133"
ms.assetid: f6295626-dd63-408c-ab5f-76367f94d6ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos &#39;AddHandler&#39; e &#39;RemoveHandler&#39; devem ter exatamente um par&#226;metro
Uma declaração de evento personalizado deve ter `AddHandler` ou `RemoveHandler` declarações, cada um deles usa um único parâmetro do tipo delegado especificado pelo evento personalizado `As` cláusula.  
  
 **ID do erro:** BC31133  
  
### Para corrigir este erro  
  
-   Remova os parâmetros extras da lista de parâmetros e alterar o tipo de parâmetro para ser o mesmo que o tipo de delegado especificado no evento personalizado `As` cláusula.  
  
## Exemplo  
 Este exemplo mostra um evento personalizado com os tipos corretos de parâmetro para o `AddHandler` e `RemoveHandler` declarações.  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## Consulte também  
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- excluir](http://msdn.microsoft.com/pt-br/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)