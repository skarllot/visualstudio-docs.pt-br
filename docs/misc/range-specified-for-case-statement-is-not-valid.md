---
title: "O intervalo especificado para a instru&#231;&#227;o &#39;Case&#39; n&#227;o &#233; v&#225;lido | Microsoft Docs"
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
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O intervalo especificado para a instru&#231;&#227;o &#39;Case&#39; n&#227;o &#233; v&#225;lido
Um intervalo inválido foi especificado para um `Case` instrução.  
  
 Quando você está comparando a mesma expressão para diversos valores diferentes, você pode usar o `Select...Case` instruções como uma alternativa para o `If...Then...Else` instruções. Enquanto o `If` e `ElseIf` instruções podem avaliar uma expressão diferente em cada instrução, o `Select` instrução avalia uma única expressão apenas uma vez e usa\-a para cada comparação. Cada `Case` instrução pode conter mais de um valor, um intervalo de valores ou uma combinação de valores e operadores de comparação.  
  
 **ID do erro:** BC40052  
  
### Para corrigir este erro  
  
-   Modificar o intervalo para incluir todos os valores, ou use um `Case Else` instrução para capturar um valor indefinido.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Estruturas de decisão](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)