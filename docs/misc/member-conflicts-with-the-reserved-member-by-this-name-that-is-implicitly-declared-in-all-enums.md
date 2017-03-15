---
title: "&#39;&lt; membro &gt;&#39; est&#225; em conflito com o membro reservado por esse nome declarado implicitamente em todos os enums | Microsoft Docs"
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
  - "bc31420"
  - "vbc31420"
helpviewer_keywords: 
  - "BC31420"
ms.assetid: f2ea5a8b-f63c-4c93-bfac-418ae5a150a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; membro &gt;&#39; est&#225; em conflito com o membro reservado por esse nome declarado implicitamente em todos os enums
O nome de um conflito de membro de tipo com o nome de um membro declarado implicitamente em todas as enumerações.  
  
 O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador cria membros implícitos correspondentes a certos elementos de programação que você declarar. Enumerações declaram implicitamente o membro `value__member`.  
  
 **ID do erro:** BC31420  
  
### Para corrigir este erro  
  
-   Modifique o nome do membro.  
  
## Consulte também  
 [Instruções de NotInBuild:Declaration no Visual Basic](http://msdn.microsoft.com/pt-br/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Visão geral de enumerações](/dotnet/visual-basic/programming-guide/language-features/constants-enums/enumerations-overview)   
 [Nomes de elemento declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)