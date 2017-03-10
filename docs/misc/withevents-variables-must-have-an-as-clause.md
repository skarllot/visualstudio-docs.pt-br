---
title: "Vari&#225;veis &#39;WithEvents&#39; devem ter uma cl&#225;usula &#39;As&#39; | Microsoft Docs"
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
  - "vbc30412"
  - "bc30412"
helpviewer_keywords: 
  - "BC30412"
ms.assetid: 8c941523-8e5d-4bf0-8a52-772ecd5d5592
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;veis &#39;WithEvents&#39; devem ter uma cl&#225;usula &#39;As&#39;
Você não forneceu um `As` cláusula com a palavra\-chave `WithEvents`. Declare a variável como a classe específica que pode lançar os eventos.  
  
 **ID do erro:** BC30412  
  
### Para corrigir este erro  
  
1.  Adicionar o `As` cláusula que especifica a classe que pode lançar os eventos.  
  
## Consulte também  
 [NÃO na compilação: WithEvents e a cláusula Handles](http://msdn.microsoft.com/pt-br/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)