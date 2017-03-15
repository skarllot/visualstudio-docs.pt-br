---
title: "&#39;Exit Sub&#39; n&#227;o &#233; v&#225;lido em uma fun&#231;&#227;o ou propriedade | Microsoft Docs"
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
  - "bc30065"
  - "vbc30065"
helpviewer_keywords: 
  - "BC30065"
ms.assetid: d6426861-ba64-4dca-9100-262c6c058bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Sub&#39; n&#227;o &#233; v&#225;lido em uma fun&#231;&#227;o ou propriedade
`Exit Sub` aparece em uma `Function` procedimento ou uma `Property` procedimento. Um `Exit` instrução deve coincidir com o bloco no qual ele ocorre.  
  
 **ID do erro:** BC30065  
  
### Para corrigir este erro  
  
-   Substitua o `Exit Sub` com o `Exit Function` ou `Exit Property` instrução conforme apropriado.  
  
## Consulte também  
 [Subprocedimentos](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimentos de função](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)