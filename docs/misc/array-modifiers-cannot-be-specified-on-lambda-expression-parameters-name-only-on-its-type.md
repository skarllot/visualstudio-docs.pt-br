---
title: "Modificadores de matriz n&#227;o podem ser especificados em nome de par&#226;metros de express&#245;es lambda, somente em seu tipo | Microsoft Docs"
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
  - "vbc36643"
  - "bc36643"
helpviewer_keywords: 
  - "BC36643"
ms.assetid: 34b6141b-6eab-4641-a3f4-53ef28c1792b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Modificadores de matriz n&#227;o podem ser especificados em nome de par&#226;metros de express&#245;es lambda, somente em seu tipo
Argumentos de matriz podem ser enviados para expressões lambda, mas a declaração de parâmetro deve incluir o tipo de elemento.  
  
```vb#  
' Not valid.  
' Dim arrayExample1 = Function(arrayPara()) 2  
  
' Valid.  
Dim arrayExample2 = Function(arrayPara() As Integer) arrayPara.Length > 0  
Dim arrayexample3 = Function(arrayPara As Integer()) arrayPara.Length > 0  
```  
  
 **ID do erro:** BC36643  
  
### Para corrigir este erro  
  
-   Especifique o tipo dos elementos no parâmetro de matriz.  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)