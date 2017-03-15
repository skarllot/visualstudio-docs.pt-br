---
title: "Argumento &#39;NPer&#39; deve ser maior que zero | Microsoft Docs"
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
  - "vbrRate_NPerMustBeGTZero"
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumento &#39;NPer&#39; deve ser maior que zero
O `NPer` função, que retorna um `Double` especificando o número de períodos de uma anuidade com base em pagamentos fixos periódicos e uma taxa de juros fixa exige um argumento maior que zero.  
  
### Para corrigir este erro  
  
-   Verifique a ortografia dos argumentos na expressão. Um nome de variável incorreta implicitamente pode criar uma variável numérica que é inicializada com zero.  
  
-   Cheque operações anteriores em variáveis na expressão, especialmente aquelas de outros procedimentos passadas para o procedimento como argumentos.  
  
## Consulte também  
 [NÃO está em compilação: Função de NPer](http://msdn.microsoft.com/pt-br/56567d16-29f7-4928-b05f-b4cd56d4fd42)   
 [Passando argumentos por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)