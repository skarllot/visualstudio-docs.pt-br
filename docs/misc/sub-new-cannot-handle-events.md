---
title: "&#39;Sub New&#39; n&#227;o pode tratar eventos | Microsoft Docs"
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
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; n&#227;o pode tratar eventos
Você tentou combinar `Sub New` com `Handles`, que é inválido. Use o `Handles` palavra\-chave no final de uma declaração de procedimento faz com que ele manipule eventos causados por uma variável de objeto declarado usando a `WithEvents` palavra\-chave.  
  
 **ID do erro:** BC30497  
  
### Para corrigir este erro  
  
1.  Não use `New` neste contexto.  
  
## Consulte também  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)