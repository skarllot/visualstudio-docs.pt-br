---
title: "Instru&#231;&#227;o &#39;Return&#39; em um m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; n&#227;o pode retornar um valor | Microsoft Docs"
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
  - "bc30940"
  - "vbc30940"
helpviewer_keywords: 
  - "BC30940"
ms.assetid: 0e4d037a-2d20-40e4-8ead-6d709d1c9c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o &#39;Return&#39; em um m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; n&#227;o pode retornar um valor
O `AddHandler`, `RemoveHandler`, e `RaiseEvent` métodos em um `Custom Event` declaração pode conter `Return` instruções para sair do método. No entanto, o `Return` instrução não pode especificar um valor de retorno porque os métodos não podem retornar valores.  
  
 **ID do erro:** BC30940  
  
### Para corrigir este erro  
  
-   Remova a expressão após o `Return` instrução.  
  
## Consulte também  
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- excluir](http://msdn.microsoft.com/pt-br/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- excluir](http://msdn.microsoft.com/pt-br/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Instrução Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)