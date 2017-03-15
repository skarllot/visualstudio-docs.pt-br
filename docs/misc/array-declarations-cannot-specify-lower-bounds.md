---
title: "Declara&#231;&#245;es de matriz n&#227;o podem especificar limites inferiores | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#245;es de matriz n&#227;o podem especificar limites inferiores
Matrizes sempre têm um limite inferior de zero. Você pode especificar zero como o limite inferior para tornar seu código mais legível. No entanto, é possível especificar qualquer outro valor para o limite inferior.  
  
 **ID do erro:** BC30805  
  
### Para corrigir este erro  
  
-   Matrizes como menos que o número total de elementos de dimensão. Por exemplo, `Dim y(6)` tem o mesmo tamanho \(7 elementos\) como `Dim x(3 To 9)`. Você também pode especificar `Dim y(0 To 6)`.  
  
-   Deslocamentos de uso para simular limites inferiores do zero. O exemplo a seguir simula uma matriz dimensionada de 3 a 9.  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## Consulte também  
 [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Dimensões de matriz no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions)   
 [NOTINBUILD como: especificar um limite inferior Zero em uma matriz](http://msdn.microsoft.com/pt-br/20ffd49a-64f7-4634-8ed0-46ba1049d935)