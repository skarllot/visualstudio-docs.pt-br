---
title: "&#39;New&#39; n&#227;o pode ser usado em uma interface | Microsoft Docs"
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
  - "vbc30375"
  - "bc30375"
helpviewer_keywords: 
  - "BC30375"
ms.assetid: c1e06108-1b52-4cbe-8cae-e816a0dbac0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; n&#227;o pode ser usado em uma interface
Um [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement) usa um [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator) cláusula ao declarar uma variável de um tipo de interface.  
  
 Embora uma interface é um tipo de referência, é possível criar uma instância dela. Você pode usar `New` para criar uma instância de uma classe ou estrutura.  
  
 **ID do erro:** BC30375  
  
### Para corrigir este erro  
  
1.  Se a variável for de um tipo de interface, remova o `New` palavra\-chave.  
  
2.  Se a variável é referir\-se a uma instância, declará\-la para ser de um tipo de classe ou estrutura. Manter o `New` palavra\-chave para criar uma instância.  
  
## Consulte também  
 [Instrução Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Instrução Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)