---
title: "&lt; type1 &gt; &#39;&lt; typename1 &gt;&#39; est&#225; em conflito com um membro implicitamente declarado para o evento &#39;&lt; eventname &gt;&#39; em &lt; type2 &gt; &#39;&lt; typename2 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31061"
  - "bc31061"
helpviewer_keywords: 
  - "BC31061"
ms.assetid: de5b1121-8c8f-4aba-a3e7-1e3e60df0dc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; type1 &gt; &#39;&lt; typename1 &gt;&#39; est&#225; em conflito com um membro implicitamente declarado para o evento &#39;&lt; eventname &gt;&#39; em &lt; type2 &gt; &#39;&lt; typename2 &gt;&#39;
O nome de um conflito de membro de tipo com o nome de um membro implicitamente criado para um evento. Eventos implicitamente criam diversas variáveis implícitas. Por exemplo, a declaração `Event X` declara implicitamente os nomes `XEventHandler`, `XEvent`, `add_X`, e `remove_X`.  
  
 **ID do erro:** BC31061  
  
### Para corrigir este erro  
  
-   Renomeie o membro declarado explicitamente para remover o conflito de nomes.  
  
## Consulte também  
 [Instruções de NotInBuild:Declaration no Visual Basic](http://msdn.microsoft.com/pt-br/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)