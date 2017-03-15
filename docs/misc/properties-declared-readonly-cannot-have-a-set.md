---
title: "As propriedades declaradas &#39;ReadOnly&#39; n&#227;o pode ter &#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# As propriedades declaradas &#39;ReadOnly&#39; n&#227;o pode ter &#39;Set&#39;
O `Set` procedimento grava o valor de uma propriedade.`ReadOnly` propriedades não podem ser gravadas.  
  
 **ID do erro:** BC30022  
  
### Para corrigir este erro  
  
-   Remover o `ReadOnly` palavra\-chave from a `Property` instrução, ou remova o `Set` procedimento do corpo da propriedade.  
  
## Consulte também  
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)