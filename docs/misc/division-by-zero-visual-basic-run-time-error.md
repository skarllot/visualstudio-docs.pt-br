---
title: "Divis&#227;o por zero (erro de tempo de execu&#231;&#227;o do Visual Basic) | Microsoft Docs"
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
  - "vbrID11"
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Divis&#227;o por zero (erro de tempo de execu&#231;&#227;o do Visual Basic)
Uma expressão que está sendo usada como um divisor tem um valor de zero.  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia das variáveis na expressão. Um nome de variável incorreta implicitamente pode criar uma variável numérica que é inicializada com zero.  
  
2.  Cheque operações anteriores em variáveis na expressão, especialmente aquelas de outros procedimentos passadas para o procedimento como argumentos.  
  
## Consulte também  
 [Passando argumentos por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/pt-br/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)