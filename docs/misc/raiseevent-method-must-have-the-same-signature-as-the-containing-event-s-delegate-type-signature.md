---
title: "O m&#233;todo &#39;RaiseEvent&#39; deve ter a mesma assinatura que o tipo de delegado do evento recipiente &#39;&lt; assinatura &gt;&#39; | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo &#39;RaiseEvent&#39; deve ter a mesma assinatura que o tipo de delegado do evento recipiente &#39;&lt; assinatura &gt;&#39;
Um `Custom Event` declaração deve ter `RaiseEvent` declaração que tem a mesma assinatura do tipo delegado especificado pelo evento personalizado `As` cláusula.  
  
 Para que as assinaturas correspondam, o `RaiseEvent` declaração e o delegado devem ter o número de parâmetros e os tipos de parâmetros devem corresponder.  
  
 **ID do erro:** BC31137  
  
### Para corrigir este erro  
  
-   Alterar os parâmetros do `RaiseEvent` declaração para corresponder aos parâmetros do tipo delegado.  
  
## Exemplo  
 Este exemplo mostra um evento personalizado com os tipos corretos de parâmetro para o `RaiseEvent` declaração.  
  
 [!CODE [VbVbalrEventError#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#2)]  
  
## Consulte também  
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [RaiseEvent \- excluir](http://msdn.microsoft.com/pt-br/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)