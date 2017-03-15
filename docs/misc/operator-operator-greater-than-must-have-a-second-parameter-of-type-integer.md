---
title: "O operador &#39;&lt; operador &gt;&#39; deve ter um segundo par&#226;metro do tipo &#39;Integer&#39; | Microsoft Docs"
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
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O operador &#39;&lt; operador &gt;&#39; deve ter um segundo par&#226;metro do tipo &#39;Integer&#39;
Um operador de deslocamento de bits é declarado com o segundo parâmetro de um tipo diferente de `Integer`.  
  
 Quando você usa o deslocamento para a direita \(`>>`\) ou shift esquerda \(`<<`\) operador em uma expressão, você especificar o tamanho do deslocamento no segundo operando. Para este operando, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] permite que você forneça qualquer tipo de dados que amplia para `Integer`. No entanto, a definição do segundo operando é estritamente `Integer`. Se você definir uma classe ou estrutura com um operador de deslocamento de bits nessa classe ou estrutura, sua definição deve especificar `Integer` para o segundo operando.  
  
 **ID do erro:** BC33041  
  
### Para corrigir este erro  
  
-   Altere a definição do operador de deslocamento de bits para retornar um `Integer` valor.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores Bit Shift](/dotnet/visual-basic/language-reference/operators/bit-shift-operators)