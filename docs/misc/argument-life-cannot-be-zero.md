---
title: "O argumento &#39;Life&#39; n&#227;o pode ser zero | Microsoft Docs"
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
  - "vbrFinancial_LifeNEZero"
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O argumento &#39;Life&#39; n&#227;o pode ser zero
Um argumento para `Life`, que deve ser um `Double` que especifica o período de vida útil do ativo, não é válido.  
  
### Para corrigir este erro  
  
-   Verifique a ortografia dos argumentos na expressão. Um nome de variável incorreta implicitamente pode criar uma variável numérica que é inicializada com zero.  
  
-   Cheque operações anteriores em variáveis na expressão, especialmente aquelas de outros procedimentos passadas para o procedimento como argumentos.  
  
## Consulte também  
 [NÃO está em compilação: Função do BDD](http://msdn.microsoft.com/pt-br/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [NÃO está em compilação: Função SYD](http://msdn.microsoft.com/pt-br/23c25672-f5dd-49ac-9893-4faa82634181)   
 [NÃO está em compilação: Função SLN](http://msdn.microsoft.com/pt-br/8e06130a-056e-4266-a8a9-1592b86f58d2)   
 [Passando argumentos por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)