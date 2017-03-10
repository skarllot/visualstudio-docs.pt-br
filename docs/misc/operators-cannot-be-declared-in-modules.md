---
title: "Operadores n&#227;o podem ser declarados em m&#243;dulos | Microsoft Docs"
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
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores n&#227;o podem ser declarados em m&#243;dulos
Um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) aparece em uma definição de módulo.  
  
 Você pode definir um operador como parte de uma classe ou estrutura que você está definindo. O operador deve levar essa classe ou estrutura como pelo menos um dos operandos.  
  
 Um operador deve usar uma instância de um elemento de programação como um dos operandos, e apenas classes e estruturas têm instâncias. Portanto, você não pode definir um operador como parte de qualquer outro elemento de programação.  
  
 **ID do erro:** BC33018  
  
### Para corrigir este erro  
  
-   Se você solicitar uma operação no módulo, use um [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement) para definir uma `Function` procedimento que executa a operação.  
  
-   Você também pode definir uma classe ou estrutura dentro do módulo e definir um operador na classe ou estrutura. No entanto, esse operador deve levar uma instância da classe ou estrutura como pelo menos um dos operandos.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)