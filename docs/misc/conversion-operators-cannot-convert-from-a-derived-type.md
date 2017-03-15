---
title: "Operadores de convers&#227;o n&#227;o podem converter de um tipo derivado | Microsoft Docs"
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
  - "bc33031"
  - "vbc33031"
helpviewer_keywords: 
  - "BC33031"
ms.assetid: e8cfef89-9fde-4f33-ab0d-cc2094e8b8eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores de convers&#227;o n&#227;o podem converter de um tipo derivado
Um operador de conversão é declarado com um tipo de parâmetro deriva do tipo de retorno.  
  
 Em tempo de compilação, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera uma conversão predefinida existir de qualquer tipo de referência para qualquer tipo na sua hierarquia de herança, ou seja, qualquer tipo do qual ele deriva ou que deriva dela. Tal conversão pode falhar em tempo de execução, mas o compilador não pode prever resultados de tempo de execução, que permite a tal conversão compilar.  
  
 Como o compilador considera essa conversão já está definida, ele não permite que você a redefina.  
  
 **ID do erro:** BC33031  
  
### Para corrigir este erro  
  
-   Remova a definição do operador completamente. Já está predefinido.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)