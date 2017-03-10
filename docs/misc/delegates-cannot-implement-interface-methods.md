---
title: "Delegados n&#227;o podem implementar m&#233;todos de interface | Microsoft Docs"
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
  - "bc30018"
  - "vbc30018"
helpviewer_keywords: 
  - "BC30018"
ms.assetid: 71851072-c0c7-4131-aaf7-f3e9e6a2a448
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegados n&#227;o podem implementar m&#233;todos de interface
Um delegado é um tipo de referência que aponta para um procedimento compartilhado ou um procedimento de instância de um objeto. Porque ela aponta para o procedimento pode ser alterado por atribuição, a `Delegate` instrução não oferece suporte a `Handles` ou `Implements` cláusulas.  
  
 **ID do erro:** BC30018  
  
### Para corrigir este erro  
  
-   Remover o `Implements` cláusula do `Delegate` instrução.  
  
## Consulte também  
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)