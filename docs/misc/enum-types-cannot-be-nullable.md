---
title: "Tipos de enumera&#231;&#227;o n&#227;o podem ser nulo | Microsoft Docs"
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
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de enumera&#231;&#227;o n&#227;o podem ser nulo
O tipo subjacente que é usado para declarar uma enumeração não pode ser anulável. Por exemplo, o código a seguir causa esse erro:  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **ID do erro:** BC32129  
  
### Para corrigir este erro  
  
-   Não use um tipo anulável subjacente em uma `Enum` declaração.  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Instrução Enum](/dotnet/visual-basic/language-reference/statements/enum-statement)