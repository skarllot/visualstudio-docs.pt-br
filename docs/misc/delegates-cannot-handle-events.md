---
title: "Delegados n&#227;o podem manipular eventos | Microsoft Docs"
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
  - "bc30019"
  - "vbc30019"
helpviewer_keywords: 
  - "BC30019"
ms.assetid: 7f0c7bb9-8e81-44bf-acc5-80d9785708aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegados n&#227;o podem manipular eventos
Um delegado é um tipo de referência que aponta para um procedimento compartilhado ou um procedimento de instância de um objeto. Porque ela aponta para o procedimento pode ser alterado por atribuição, a `Delegate` instrução não oferece suporte a `Handles` ou `Implements` cláusulas.  
  
 **ID do erro:** BC30019  
  
### Para corrigir este erro  
  
-   Remover o `Handles` cláusula do `Delegate` instrução.  
  
## Consulte também  
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)