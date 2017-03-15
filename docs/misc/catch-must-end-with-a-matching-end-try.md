---
title: "&#39;Catch&#39; deve finalizar com &#39;End Try&#39; correspondente | Microsoft Docs"
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
  - "bc30441"
  - "vbc30441"
helpviewer_keywords: 
  - "BC30441"
ms.assetid: 0e4756b4-1f29-4073-88c5-8f8c93ba6c9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; deve finalizar com &#39;End Try&#39; correspondente
Um `Catch` instrução aparece no seu código sem encontrar uma correspondência `End Try` instrução.`Catch` instruções devem ser concluídas com um `End Try` instrução.  
  
 **ID do erro:** BC30441  
  
### Para corrigir este erro  
  
1.  Remover o `Catch` instrução.  
  
2.  Adicione um `End Try` instrução para concluir o bloco.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Tratamento de visão geral do Visual Basic de exceções estruturado](http://msdn.microsoft.com/pt-br/bb81af80-a735-4873-9711-6151a48e418a)