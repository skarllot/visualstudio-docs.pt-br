---
title: "Tipo de par&#226;metro desse operador un&#225;rio deve ser do tipo recipiente &#39;&lt; typename &gt;&#39; | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de par&#226;metro desse operador un&#225;rio deve ser do tipo recipiente &#39;&lt; typename &gt;&#39;
Uma definição de um operador unário Especifica um parâmetro com um tipo diferente de classe ou estrutura na qual o operador está definido.  
  
 Quando você define um operador em uma classe ou estrutura, pelo menos um dos parâmetros deve ser do tipo de classe ou estrutura. No caso de um operador unário, o único operando deve ser do tipo de classe ou estrutura.  
  
 **ID do erro:** BC33020  
  
### Para corrigir este erro  
  
-   Altere o tipo de parâmetro para o tipo da classe ou estrutura na qual o operador está definido.  
  
-   Se você quiser usar um tipo de dados como um parâmetro e retornar um tipo de dados diferente como resultado da operação, defina um operador de conversão em vez disso.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)