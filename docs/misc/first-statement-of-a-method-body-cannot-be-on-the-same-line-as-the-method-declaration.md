---
title: "Primeira instru&#231;&#227;o do corpo de um m&#233;todo n&#227;o pode ser na mesma linha da declara&#231;&#227;o de m&#233;todo | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Primeira instru&#231;&#227;o do corpo de um m&#233;todo n&#227;o pode ser na mesma linha da declara&#231;&#227;o de m&#233;todo
Um `Function`, `Sub`, `Get`, `Set`, ou `Property` instrução deve ser apenas uma linha de código fonte.  
  
 **ID do erro:** BC30040  
  
### Para corrigir este erro  
  
1.  Remova qualquer rótulo de linha que precede a declaração do procedimento.  
  
2.  Mova qualquer instrução que precede a declaração do procedimento para uma linha de código de origem anterior.  
  
3.  Mova qualquer instrução seguinte a declaração do procedimento para uma linha de código de origem subsequentes.  
  
## Consulte também  
 [Procedimentos](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [Como rotular instruções](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)