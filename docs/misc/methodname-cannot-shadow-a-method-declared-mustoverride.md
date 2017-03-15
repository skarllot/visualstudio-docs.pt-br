---
title: "&#39;&lt; methodname &gt;&#39; n&#227;o pode sombrear um m&#233;todo declarado como &#39;MustOverride&#39; | Microsoft Docs"
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
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; methodname &gt;&#39; n&#227;o pode sombrear um m&#233;todo declarado como &#39;MustOverride&#39;
Uma propriedade ou método com o `MustOverride` modificador e o mesmo nome é declarado em uma classe derivada.  
  
 **ID do erro:** BC31404  
  
### Para corrigir este erro  
  
1.  Adicionar o `Overrides` modificador para a propriedade ou método na classe derivada.  
  
2.  Remover o `MustOverride` modificador da propriedade ou método na classe base.  
  
## Consulte também  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)