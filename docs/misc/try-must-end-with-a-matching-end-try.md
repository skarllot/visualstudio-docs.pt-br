---
title: "&#39;Try&#39; deve finalizar com &#39;End Try&#39; correspondente | Microsoft Docs"
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
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Try&#39; deve finalizar com &#39;End Try&#39; correspondente
`Try` é usado para iniciar um `Try` bloco; portanto, ele só pode aparecer no início do bloco, com uma correspondência`End Try` terminando o bloco de instrução. Ou você tem um redundantes `Try`, ou não terminou seu `Try` bloco com `Finally`.  
  
 **ID do erro:** BC30384  
  
### Para corrigir este erro  
  
1.  Localize e remova o estranhas `Try`, ou finalize o bloco com um correspondente `End Try`.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Tratamento de visão geral do Visual Basic de exceções estruturado](http://msdn.microsoft.com/pt-br/bb81af80-a735-4873-9711-6151a48e418a)