---
title: "A propriedade &#39;ReadOnly&#39; deve fornecer &#39;Get&#39; | Microsoft Docs"
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
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A propriedade &#39;ReadOnly&#39; deve fornecer &#39;Get&#39;
Se uma propriedade é declarada como `ReadOnly`, ele deve fornecer um procedimento para ler o seu valor.  
  
 **ID do erro:** BC30126  
  
### Para corrigir este erro  
  
1.  Certifique\-se de incluir uma `Get` procedimento entre o `Property` instrução e `End Property` instrução.  
  
2.  Verifique se que outros procedimentos dentro do `Property` declaração são terminadas corretamente.  
  
## Consulte também  
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement)