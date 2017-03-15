---
title: "Operadores de convers&#227;o n&#227;o podem converter objeto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33028"
  - "vbc33028"
helpviewer_keywords: 
  - "BC33028"
ms.assetid: 064b478c-85a1-4e13-a292-d8aebb079cad
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores de convers&#227;o n&#227;o podem converter objeto
Um operador de conversão é declarado com um tipo de retorno de [Tipo de dados Object](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Em tempo de compilação, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera uma conversão predefinida existir de qualquer tipo de referência para qualquer tipo na sua hierarquia de herança, ou seja, qualquer tipo do qual ele deriva ou que deriva dela.`Object` é o tipo de dados universal no [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], portanto, todo tipo deriva de `Object`.  
  
 Como o compilador considera essa conversão já está definida, ele não permite que você a redefina.  
  
 **ID do erro:** BC33028  
  
### Para corrigir este erro  
  
-   Remova a definição do operador completamente. Já está predefinido.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Objeto como o tipo de dados Universal \(Visual Basic\)](http://msdn.microsoft.com/pt-br/5315bf21-2b22-45ab-98cd-5631dffbcb2f)