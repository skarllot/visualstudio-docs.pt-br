---
title: "&#39;Exit AddHandler&#39;, &#39;Exit RemoveHandler&#39; e &#39;Exit RaiseEvent&#39; n&#227;o s&#227;o v&#225;lidos | Microsoft Docs"
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
  - "vbc31111"
  - "bc31111"
helpviewer_keywords: 
  - "BC31111"
ms.assetid: e02264f3-0645-4de5-b622-8a2a74496b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit AddHandler&#39;, &#39;Exit RemoveHandler&#39; e &#39;Exit RaiseEvent&#39; n&#227;o s&#227;o v&#225;lidos
'Exit AddHandler', 'Exit RemoveHandler' e 'Exit RaiseEvent' não são válidas. Use 'Return' para sair dos membros do evento.  
  
 O `Exit` instrução não pode ser usada para sair `AddHandler`, `RemoveHandler`, ou `RaiseEvent` métodos em um `Custom Event` declaração. Em vez disso, use o `Return` instrução, sem especificar uma expressão de retornada, para sair do método.  
  
 **ID do erro:** BC31111  
  
### Para corrigir este erro  
  
-   Substitua o `Exit` instrução com um `Return` instrução.  
  
     Verifique se o `Return` instrução não especificar uma expressão de retornada.  
  
## Consulte também  
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- excluir](http://msdn.microsoft.com/pt-br/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- excluir](http://msdn.microsoft.com/pt-br/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Instrução Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)