---
title: "&#39;&lt; typename &gt;&#39; deve ser declarado &#39;MustInherit&#39; porque ele cont&#233;m m&#233;todos declarados &#39;MustOverride&#39; | Microsoft Docs"
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
  - "vbc31411"
  - "bc31411"
helpviewer_keywords: 
  - "BC31411"
ms.assetid: 5a9f4c57-a4b8-45f5-8273-b7caa689a170
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; deve ser declarado &#39;MustInherit&#39; porque ele cont&#233;m m&#233;todos declarados &#39;MustOverride&#39;
Tipos que contenham `MustOverride` membros devem ser declarados como `MustInherit`.  
  
 **ID do erro:** BC31411  
  
### Para corrigir este erro  
  
-   Adicionar o `MustInherit` modificador no tipo.  
  
## Consulte também  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)