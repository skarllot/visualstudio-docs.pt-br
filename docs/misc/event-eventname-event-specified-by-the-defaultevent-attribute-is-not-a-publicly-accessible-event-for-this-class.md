---
title: "Evento &#39;&lt; eventname &gt;&#39; especificado pelo atributo &#39;DefaultEvent&#39; n&#227;o &#233; um evento publicamente acess&#237;vel para esta classe | Microsoft Docs"
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
  - "vbc30770"
  - "bc30770"
helpviewer_keywords: 
  - "BC30770"
ms.assetid: 7524fba7-2a37-4bc3-b789-87d73a166575
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Evento &#39;&lt; eventname &gt;&#39; especificado pelo atributo &#39;DefaultEvent&#39; n&#227;o &#233; um evento publicamente acess&#237;vel para esta classe
O <xref:System.ComponentModel.DefaultEventAttribute> atributo deve especificar o nome do evento publicamente acessível na classe à qual o atributo é aplicado.  
  
 **ID do erro:** BC30770  
  
### Para corrigir este erro  
  
1.  Verifique se que a classe define um evento publicamente acessível.  
  
2.  Certifique\-se de que o nome do evento na classe coincide com o nome especificado pelo <xref:System.ComponentModel.DefaultEventAttribute> atributo.  
  
## Consulte também  
 <xref:System.ComponentModel.DefaultEventAttribute>   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Público](/dotnet/visual-basic/language-reference/modifiers/public)