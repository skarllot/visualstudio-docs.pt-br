---
title: "Vari&#225;vel n&#227;o pode ser inicializada com tipo n&#227;o matriz &#39;&lt; elementname &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel n&#227;o pode ser inicializada com tipo n&#227;o matriz &#39;&lt; elementname &gt;&#39;
Uma variável que é declarada como uma matriz deve ser inicializada com um valor de matriz.  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **ID do erro:** BC36536  
  
### Para corrigir este erro  
  
-   Inicialize a variável de matriz com um valor de matriz:  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## Consulte também  
 [NOTINBUILD uma variável de matriz](http://msdn.microsoft.com/pt-br/c2da78bd-6928-46ba-805f-44f819dfaf93)