---
title: "O par&#226;metro &#39;&lt; parametername &gt;&#39; j&#225; tem um argumento omitido correspondente | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro &#39;&lt; parametername &gt;&#39; j&#225; tem um argumento omitido correspondente
Uma chamada de procedimento fornece um argumento pelo nome após omitindo o mesmo argumento por posição. A seguir está um exemplo:  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **ID do erro:** BC36566  
  
### Para corrigir este erro  
  
-   Forneça o argumento por posição, ou remova a vírgula que omiti\-lo.  
  
## Consulte também  
 [Passando argumentos por posição e nome](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)