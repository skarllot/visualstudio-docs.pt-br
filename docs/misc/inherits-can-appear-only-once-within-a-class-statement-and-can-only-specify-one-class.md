---
title: "&#39;Inherits&#39; pode aparecer apenas uma vez em uma instru&#231;&#227;o &#39;Class&#39; e pode especificar apenas uma classe | Microsoft Docs"
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
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Inherits&#39; pode aparecer apenas uma vez em uma instru&#231;&#227;o &#39;Class&#39; e pode especificar apenas uma classe
Mais de um `Inherits` instrução aparece na mesma classe, ou um `Inherits` declaração especifica mais de uma classe. Uma classe pode herdar apenas uma classe base.  
  
 **ID do erro:** BC30121  
  
### Para corrigir este erro  
  
-   Remova qualquer extra `Inherits` instruções e verifique se o restante `Inherits` declaração especifica apenas uma classe base.  
  
## Consulte também  
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)