---
title: "&#39;Select Case&#39; deve finalizar com &#39;End Select&#39; correspondente | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select Case&#39; deve finalizar com &#39;End Select&#39; correspondente
Um `Select` ou `Select Case` declaração ocorre sem um correspondente `End Select` instrução. Um `End Select` declaração deve ser usada para encerrar o `Select` bloco.  
  
 **ID do erro:** BC30095  
  
### Para corrigir este erro  
  
1.  Se este `Select` bloco faz parte de um conjunto de aninhada `Select` blocos, certifique\-se de cada bloco é terminado de maneira apropriada.  
  
2.  Adicione um `End Select` instrução ao final do `Select` bloco.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)