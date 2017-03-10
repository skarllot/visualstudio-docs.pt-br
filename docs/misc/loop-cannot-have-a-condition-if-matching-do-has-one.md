---
title: "&#39;Loop&#39; n&#227;o pode ter uma condi&#231;&#227;o se &#39;Do&#39; correspondente tiver uma | Microsoft Docs"
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
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Loop&#39; n&#227;o pode ter uma condi&#231;&#227;o se &#39;Do&#39; correspondente tiver uma
Um `Loop` instrução contém um `While` ou `Until` cláusula e correspondente `Do` instrução também contém tal cláusula. Somente um da `Do` e `Loop` as instruções em um loop podem especificar uma condição.  
  
 **ID do erro:** BC30238  
  
### Para corrigir este erro  
  
-   Remover o `While` ou `Until` cláusula do `Do` instrução ou o `Loop` instrução.  
  
## Consulte também  
 [Instrução Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)