---
title: "&#39;With&#39; deve finalizar com um &#39;End With&#39; correspondente | Microsoft Docs"
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
  - "bc30085"
  - "vbc30085"
helpviewer_keywords: 
  - "BC30085"
ms.assetid: aa88f4d0-be5f-4efe-a4ef-80e6d6124e6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;With&#39; deve finalizar com um &#39;End With&#39; correspondente
Um `With` declaração ocorre sem um correspondente `End With` instrução. Um `End With` declaração deve ser usada para encerrar o `With` bloco.  
  
 **ID do erro:** BC30085  
  
### Para corrigir este erro  
  
-   Se este `With` bloco faz parte de um conjunto de aninhada `With` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
-   Adicione um `End With` instrução ao final do `With` bloco.  
  
## Consulte também  
 [Instrução With ... End With](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)