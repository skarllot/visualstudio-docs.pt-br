---
title: "M&#233;todo &#39;MustOverride&#39; &#39;&lt; methodname &gt;&#39; n&#227;o pode ser chamado com &#39;MyClass&#39; | Microsoft Docs"
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
  - "bc30614"
  - "vbc30614"
helpviewer_keywords: 
  - "BC30614"
ms.assetid: fc57af41-1552-46d1-9727-341f1835e661
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todo &#39;MustOverride&#39; &#39;&lt; methodname &gt;&#39; n&#227;o pode ser chamado com &#39;MyClass&#39;
`MyClass` é equivalente a `Me`, mas todas as invocações do método nele são tratadas como se fosse o método está sendo chamado `NotOverridable`.  
  
 **ID do erro:** BC30614  
  
### Para corrigir este erro  
  
-   Remover o `MustOverride` modificador, declarar o método na classe base e herdam e substituir essa classe.  
  
## Consulte também  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)