---
title: "Operadores de convers&#227;o n&#227;o podem converter de um tipo de interface | Microsoft Docs"
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
  - "vbc33029"
  - "bc33029"
helpviewer_keywords: 
  - "BC33029"
ms.assetid: 0d0ee461-dd48-424b-b83a-484bfc648d4d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores de convers&#227;o n&#227;o podem converter de um tipo de interface
Um operador de conversão é declarado com um tipo de interface para o parâmetro.  
  
 Em tempo de compilação, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera uma conversão predefinida existir de qualquer interface para qualquer tipo de referência. Tal conversão pode falhar em tempo de execução, mas o compilador não pode prever resultados de tempo de execução, que permite a tal conversão compilar.  
  
 Como o compilador considera essa conversão já está definida, ele não permite que você a redefina.  
  
 **ID do erro:** BC33029  
  
### Para corrigir este erro  
  
-   Remova a definição do operador completamente. Já está predefinido.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)