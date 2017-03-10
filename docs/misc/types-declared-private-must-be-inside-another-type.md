---
title: "Tipos declarados &#39;Private&#39; deve estar dentro de outro tipo | Microsoft Docs"
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
  - "vbc31089"
  - "bc31089"
helpviewer_keywords: 
  - "BC31089"
ms.assetid: 44ea5fe4-4af6-4cea-a4a5-2cf966df2937
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos declarados &#39;Private&#39; deve estar dentro de outro tipo
O `Private` modificador foi usado em um tipo não dentro de outro tipo.  
  
 **ID do erro:** BC31089  
  
### Para corrigir este erro  
  
1.  Use um modificador de acesso menos restritivo, como `Friend`.  
  
2.  Declare o tipo em outro tipo.  
  
## Consulte também  
 [Particular](/dotnet/visual-basic/language-reference/modifiers/private)