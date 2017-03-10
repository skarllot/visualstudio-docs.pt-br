---
title: "A instru&#231;&#227;o n&#227;o declara um m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A instru&#231;&#227;o n&#227;o declara um m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39;
A instrução não fornecer um `AddHandler`, `RemoveHandler`, ou `RaiseEvent` declaração em torno de uma `Custom Event` procedimento. Uma declaração de evento personalizado é um bloco de código entre o `Custom Event` e `End Event` instruções. Dentro deste bloco, cada `Custom Event` procedimento aparece como um bloco interno envolto em uma instrução de declaração e uma `End` instrução.  
  
 **ID do erro:** BC31113  
  
### Para corrigir este erro  
  
-   Forneça um `AddHandler`, `RemoveHandler`, ou `RaiseEvent` uma instrução de declaração.  
  
## Consulte também  
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- excluir](http://msdn.microsoft.com/pt-br/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- excluir](http://msdn.microsoft.com/pt-br/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)