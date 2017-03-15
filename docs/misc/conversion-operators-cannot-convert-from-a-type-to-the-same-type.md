---
title: "Operadores de convers&#227;o n&#227;o podem converter de um tipo para o mesmo tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33024"
  - "vbc33024"
helpviewer_keywords: 
  - "BC33024"
ms.assetid: 4b47bcb0-4f0c-4d1c-9274-cce5b8e2b370
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores de convers&#227;o n&#227;o podem converter de um tipo para o mesmo tipo
Um operador de conversão é declarado com o mesmo tipo para o parâmetro e retorno.  
  
 Não é significativa para converter de qualquer tipo a mesmo.  
  
 **ID do erro:** BC33024  
  
### Para corrigir este erro  
  
-   Altere o tipo de parâmetro ou o valor de retorno. Um deles deve ser do tipo de classe ou estrutura na qual o operador é definido. O outro deve ser de um tipo diferente.  
  
-   Se você precisar executar uma transformação no conteúdo do parâmetro, use um [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement) para definir uma `Function` procedimento em vez de um operador.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)