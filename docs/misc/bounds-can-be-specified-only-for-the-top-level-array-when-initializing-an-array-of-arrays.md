---
title: "Limites podem ser especificados somente para a matriz de n&#237;vel superior ao inicializar uma matriz de matrizes | Microsoft Docs"
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
  - "bc32014"
  - "vbc32014"
helpviewer_keywords: 
  - "BC32014"
ms.assetid: d8d7155d-82d1-4a25-b9bb-1883e1586383
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Limites podem ser especificados somente para a matriz de n&#237;vel superior ao inicializar uma matriz de matrizes
Uma inicialização de matriz para uma matriz denteada \(matriz de matrizes\) define o tamanho inicial de um dos níveis inferiores. Você pode especificar o comprimento de apenas a matriz de nível superior na instrução de declaração de matriz.  
  
 **ID do erro:** BC32014  
  
### Para corrigir este erro  
  
1.  Remova a especificação do comprimento de todos, mas a matriz de nível superior.  
  
2.  Defina o tamanho inicial de matrizes de nível inferior em instruções de atribuição subsequente usando o `New` palavra\-chave.  
  
## Consulte também  
 [NOTINBUILD uma variável de matriz](http://msdn.microsoft.com/pt-br/c2da78bd-6928-46ba-805f-44f819dfaf93)   
 [NOTINBUILD denteadas matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/05c12439-ee8f-4fef-ba75-b35402b67ab9)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)