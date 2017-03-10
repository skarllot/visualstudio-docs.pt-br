---
title: "Vari&#225;veis locais dentro de m&#233;todos de estruturas n&#227;o podem ser declaradas &#39;Static&#39; | Microsoft Docs"
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
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;veis locais dentro de m&#233;todos de estruturas n&#227;o podem ser declaradas &#39;Static&#39;
O `Static` modificador não pode ser usado com variáveis locais nas estruturas.  
  
 **ID do erro:** BC31400  
  
### Para corrigir este erro  
  
1.  Remover o `Static` modificador da variável local.  
  
2.  Declare a variável como uma variável estática com escopo mais amplo.  
  
## Consulte também  
 [Estático](/dotnet/visual-basic/language-reference/modifiers/static)