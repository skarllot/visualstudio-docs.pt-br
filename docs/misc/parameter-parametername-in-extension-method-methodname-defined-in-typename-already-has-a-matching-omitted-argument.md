---
title: "O par&#226;metro &#39;&lt; parametername &gt;&#39; no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; typename &gt;&#39; j&#225; tem um argumento omitido correspondente | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro &#39;&lt; parametername &gt;&#39; no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; typename &gt;&#39; j&#225; tem um argumento omitido correspondente
Uma chamada de procedimento para um método de extensão omite um argumento por posição e, em seguida, fornece o argumento pelo nome. Por exemplo, a seguinte chamada ao método de extensão `ABC` primeiro omite um argumento para o parâmetro `Y`, e, em seguida, fornece ele pelo nome.  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **ID do erro:** BC36583  
  
### Para corrigir este erro  
  
-   Forneça o argumento por posição, ou remova a vírgula que omiti\-lo.  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Passando argumentos por posição e nome](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)