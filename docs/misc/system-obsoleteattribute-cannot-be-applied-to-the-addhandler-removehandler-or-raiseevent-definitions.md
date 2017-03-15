---
title: "&#39;System. ObsoleteAttribute&#39; n&#227;o pode ser aplicado &#224;s defini&#231;&#245;es &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System. ObsoleteAttribute&#39; n&#227;o pode ser aplicado &#224;s defini&#231;&#245;es &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39;
'System. ObsoleteAttribute' não pode ser aplicado às definições 'AddHandler', 'RemoveHandler' ou 'RaiseEvent'. Se necessário, aplique o atributo diretamente ao evento.  
  
 Um evento personalizado se aplica a <xref:System.ObsoleteAttribute> para sua `AddHandler`, `RemoveHandler`, ou `RaiseEvent` procedimento.  
  
 O <xref:System.ObsoleteAttribute> marca um elemento de programação como não mais em uso e informa aos usuários que o elemento está para ser removido em futuras versões do produto.  
  
 Não faz sentido ter algumas partes de um evento personalizado ainda em uso, enquanto outros não estão mais em uso.  
  
 **ID do erro:** BC31142  
  
### Para corrigir este erro  
  
-   Remover o <xref:System.ObsoleteAttribute> da declaração individual de procedimento e aplique\-à declaração final do evento.  
  
## Consulte também  
 <xref:System.ObsoleteAttribute>   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Instrução AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Instrução RemoveHandler](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Instrução RaiseEvent](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)