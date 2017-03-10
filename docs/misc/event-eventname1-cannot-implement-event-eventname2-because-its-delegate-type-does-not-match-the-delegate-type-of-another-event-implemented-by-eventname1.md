---
title: "O evento &#39;&lt; eventname1 &gt;&#39; n&#227;o pode implementar o evento &#39;&lt; eventname2 &gt;&#39; porque seu tipo delegado n&#227;o corresponde ao tipo delegado de outro evento implementado por &#39;&lt; eventname1 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O evento &#39;&lt; eventname1 &gt;&#39; n&#227;o pode implementar o evento &#39;&lt; eventname2 &gt;&#39; porque seu tipo delegado n&#227;o corresponde ao tipo delegado de outro evento implementado por &#39;&lt; eventname1 &gt;&#39;
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível implementar um evento porque o tipo delegado do evento não corresponde ao tipo delegado de outro evento. Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá\-los junto com o mesmo evento. Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando a `As` sintaxe e especifique o mesmo tipo delegado.  
  
 **ID do erro:** BC31407  
  
### Para corrigir este erro  
  
-   Implemente os eventos separadamente.  
  
## Consulte também  
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)