---
title: "Propriedades declaradas &#39;WriteOnly&#39; n&#227;o pode ter &#39;Get&#39; | Microsoft Docs"
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
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedades declaradas &#39;WriteOnly&#39; n&#227;o pode ter &#39;Get&#39;
O `Get` procedimento lê o valor de uma propriedade.`WriteOnly` propriedades não podem ser lidas.  
  
 **ID do erro:** BC30023  
  
### Para corrigir este erro  
  
-   Remover o `WriteOnly` palavra\-chave from a `Property` instrução, ou remova o `Get` procedimento do corpo da propriedade.  
  
## Consulte também  
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [WriteOnly](/dotnet/visual-basic/language-reference/modifiers/writeonly)