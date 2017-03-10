---
title: "&#39;Do&#39; deve finalizar com &#39;Loop&#39; correspondente | Microsoft Docs"
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
  - "vbc30083"
  - "bc30083"
helpviewer_keywords: 
  - "BC30083"
ms.assetid: b157b9e3-57fa-4324-a13d-b37bcf0861e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Do&#39; deve finalizar com &#39;Loop&#39; correspondente
Um `Do` declaração ocorre sem um correspondente `Loop` instrução. Um `Loop` declaração deve ser usada para encerrar o `Do` loop.  
  
 **ID do erro:** BC30083  
  
### Para corrigir este erro  
  
-   Se este `Do` loop é parte de um conjunto de loops aninhados, garanta que cada loop é terminado corretamente.  
  
-   Adicione um `Loop` instrução ao final do `Do` loop.  
  
## Consulte também  
 [Instrução Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)