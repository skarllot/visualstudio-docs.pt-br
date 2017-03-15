---
title: "M&#243;dulos n&#227;o podem ser gen&#233;ricos | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#243;dulos n&#227;o podem ser gen&#233;ricos
Um `Module` instrução usa o `Of` palavra\-chave para apresentar os parâmetros de tipo genérico.  
  
 Você pode definir e usar classes genéricas, estruturas, interfaces, procedimentos e representantes. Não é possível definir módulos genéricos.  
  
 **ID do erro:** BC32073  
  
### Para corrigir este erro  
  
1.  Remover o `Of` palavra\-chave from a `Module` instrução.  
  
2.  Se você quiser a funcionalidade de um módulo genérico, a mais próxima aproximação é uma classe genérica. Use um [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement) em vez de um `Module` instrução.  
  
## Consulte também  
 [Instrução Module](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)