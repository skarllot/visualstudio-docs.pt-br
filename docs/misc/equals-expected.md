---
title: "&#39;Equals&#39; esperado | Microsoft Docs"
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
  - "vbc36619"
  - "bc36619"
helpviewer_keywords: 
  - "BC36619"
ms.assetid: 1fd8c0dc-0e87-47b7-ab30-498809cca033
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; esperado
Um `Join` ou `Group Join` cláusula foi especificada sem um `Equals` operador. Você usa o `Equals` operador para identificar o `Boolean` operação para testar os campos de itens correspondentes.  
  
 **ID do erro:** BC36619  
  
### Para corrigir este erro  
  
1.  Adicionar o `Equals` campos de operador e a chave para o `Join` ou `Group Join` cláusula. Por exemplo:  
  
    ```vb#  
    Dim petOwnersGrouped = From pers In people _ Group Join pet In pets _ On pers Equals pet.Owner _ Into PetList = Group _ Select pers.FirstName, pers.LastName, _ PetList  
    ```  
  
## Consulte também  
 [Como combinar dados com junções](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Cláusula Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Cláusula Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)