---
title: "Par&#226;metros de m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; e &#39;RaiseEvent&#39; n&#227;o podem ser declarados como &#39;&lt; modificador &gt;&#39; | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros de m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; e &#39;RaiseEvent&#39; n&#227;o podem ser declarados como &#39;&lt; modificador &gt;&#39;
Os parâmetros de `AddHandler`, `RemoveHandler`, e `RaiseEvent` métodos não podem ser declarados com o `Optional` ou `ParamArray` modificadores.  
  
 O `Optional` ou `ParamArray` modificadores são permitidos somente em parâmetros nas `Declare`, `Function`, `Property`, e `Sub` declarações.  
  
 **ID do erro:** BC31138  
  
### Para corrigir este erro  
  
-   Remover o `Optional` ou `ParamArray` palavra\-chave da lista de parâmetros.  
  
## Consulte também  
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- excluir](http://msdn.microsoft.com/pt-br/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- excluir](http://msdn.microsoft.com/pt-br/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Opcional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)