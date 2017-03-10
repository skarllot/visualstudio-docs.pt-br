---
title: "&#39;E&#39; esperado | Microsoft Docs"
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
  - "vbc36620"
  - "bc36620"
helpviewer_keywords: 
  - "BC36620"
ms.assetid: b3d21d4d-86c0-44d2-8afc-c19d375e9ddd
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;E&#39; esperado
Um operador de comparação diferente de `And` foi usado para combinar duas ou mais `Equals` operadores em uma `Join` ou `Group Join` cláusula. Somente o `And` operador é permitido combinar vários `Equals` operadores em uma `Join` ou `Group Join` cláusula.  
  
 **ID do erro:** BC36620  
  
### Para corrigir este erro  
  
1.  Reestruturar o `Equals` cláusulas para fazer comparações usando apenas o `And` operador. Este é um exemplo:  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _  
                        Join pet In pets _  
                        On pet.Owner Equals pers And _  
                           pet.Name = pers.PetName_  
                        Select pers, pet  
    ```  
  
## Consulte também  
 [Como combinar dados com junções](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Cláusula Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Cláusula Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)