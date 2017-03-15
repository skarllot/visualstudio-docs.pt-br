---
title: "N&#227;o &#233; poss&#237;vel inferir um tipo de dados para &#39;&lt; variablename &gt;&#39; porque as dimens&#245;es de matriz n&#227;o coincidem | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel inferir um tipo de dados para &#39;&lt; variablename &gt;&#39; porque as dimens&#245;es de matriz n&#227;o coincidem
Se as dimensões usadas para inicializar uma matriz não coincidem com as dimensões na declaração, o compilador não pode inferir um tipo de dados para a matriz. Por exemplo, o código a seguir causa esse erro.  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **ID do erro:** BC36909  
  
## Consulte também  
 [Inferência de tipo local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [NOTINBUILD como: inicializar uma matriz Multidimensional](http://msdn.microsoft.com/pt-br/502dcf8b-d86c-46f1-ad7d-3ce809645774)