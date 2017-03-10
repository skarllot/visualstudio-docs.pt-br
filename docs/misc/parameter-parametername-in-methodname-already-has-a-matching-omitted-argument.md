---
title: "O par&#226;metro &#39;&lt; parametername &gt;&#39; em &#39;&lt; methodname &gt;&#39; j&#225; tem um argumento omitido correspondente | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro &#39;&lt; parametername &gt;&#39; em &#39;&lt; methodname &gt;&#39; j&#225; tem um argumento omitido correspondente
Uma chamada de procedimento fornece um argumento pelo nome após omitindo o mesmo argumento por posição. Por exemplo:  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **ID do erro:** BC32021  
  
### Para corrigir este erro  
  
-   Forneça o argumento por posição, ou remova a vírgula que omiti\-lo.  
  
## Consulte também  
 [Passando argumentos por posição e nome](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)