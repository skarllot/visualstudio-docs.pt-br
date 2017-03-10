---
title: "&#39;&lt; method &gt;&#39; n&#227;o est&#225; acess&#237;vel neste contexto porque ele &#233; &#39;&lt; modificador &gt;&#39; | Microsoft Docs"
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
  - "vbc30389"
  - "bc30389"
helpviewer_keywords: 
  - "BC30389"
ms.assetid: fae58a68-df91-4741-a8c9-f1bb10e166e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method &gt;&#39; n&#227;o est&#225; acess&#237;vel neste contexto porque ele &#233; &#39;&lt; modificador &gt;&#39;
Você tentou acessar um método que não está acessível neste contexto porque ele foi declarado `Private`. Uma possível causa desse erro é que o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador importa todos os membros de uma classe e diferencia maiúsculas de minúsculas para nomes diferenciados apenas por maiúsculas e minúsculas entrem em conflito.  
  
 **ID do erro:** BC30389  
  
### Para corrigir este erro  
  
-   Considere declarar o método `Public`.  
  
-   Se o erro é causado por uma colisão de nomes, diferencie os nomes de colisão por mais do que o caso.  
  
## Consulte também  
 [Particular](/dotnet/visual-basic/language-reference/modifiers/private)