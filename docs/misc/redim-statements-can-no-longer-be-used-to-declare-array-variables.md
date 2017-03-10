---
title: "Instru&#231;&#245;es &#39;ReDim&#39; n&#227;o podem ser usadas para declarar vari&#225;veis de matriz | Microsoft Docs"
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
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es &#39;ReDim&#39; n&#227;o podem ser usadas para declarar vari&#225;veis de matriz
`ReDim` só pode ser usado para alterar o tamanho de uma matriz existente.  
  
 **ID do erro:** BC30811  
  
### Para corrigir este erro  
  
-   Especifique o tamanho da matrizes quando elas são declarados; Por exemplo:  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## Consulte também  
 [Resumo de matrizes](/dotnet/visual-basic/language-reference/keywords/arrays-summary)   
 [Instrução ReDim](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/pt-br/b4da14db-ff23-490f-b3c6-d7ae1b649532)