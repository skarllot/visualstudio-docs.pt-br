---
title: "O modificador &#39;Custom&#39; n&#227;o &#233; v&#225;lido em eventos declarados em interfaces | Microsoft Docs"
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
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O modificador &#39;Custom&#39; n&#227;o &#233; v&#225;lido em eventos declarados em interfaces
Um evento personalizado não pode ser declarado em uma interface porque um evento personalizado deve fornecer uma implementação de seu `AddHandler`, `RemoverHandler`, e `RaiseEvent` métodos.  
  
 O `Custom` palavra\-chave pode ser usada em uma classe derivada que implementa o evento.  
  
 **ID do erro:** BC31121  
  
### Para corrigir este erro  
  
-   Remover o `Custom` palavra\-chave da declaração de evento na interface.  
  
## Exemplo  
 Este exemplo mostra como implementar um evento declarado em uma interface como um evento personalizado.  
  
 [!CODE [VbVbalrEventError#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#3)]  
  
## Consulte também  
 [Personalizado \- excluir](http://msdn.microsoft.com/pt-br/dc62be07-c896-4866-a533-982a661d143f)   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Instrução Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)