---
title: "&lt; methodname &gt;&#39; e &#39;&lt; methodname &gt;&#39; n&#227;o pode sobrecarregar cada um porque eles diferem em &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; methodname &gt;&#39; e &#39;&lt; methodname &gt;&#39; n&#227;o pode sobrecarregar cada um porque eles diferem em &#39;ReadOnly&#39; ou &#39;WriteOnly&#39;
Você tentou sobrecarregar dois métodos que diferem um do outro somente em suas `ReadOnly` e `WriteOnly` declarações. É possível usar algo diferente de lista de argumentos para diferenciar as versões.  
  
 **ID do erro:** BC30366  
  
### Para corrigir este erro  
  
-   Certifique\-se de que os métodos são diferenciados por mais de `ReadOnly` e `WriteOnly`.  
  
## Consulte também  
 [Considerações sobre procedimentos de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)