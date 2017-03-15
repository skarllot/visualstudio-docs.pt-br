---
title: "&#39;Join&#39; esperado | Microsoft Docs"
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
  - "vbc36631"
  - "bc36631"
helpviewer_keywords: 
  - "BC36631"
ms.assetid: bb2b03b6-6784-423a-b91a-cb7066c1d093
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Join&#39; esperado
Um `Group Join` cláusula foi especificada sem um `Join` palavra\-chave.  
  
 **ID do erro:** BC36631  
  
### Para corrigir este erro  
  
1.  Adicionar o `Join` palavra\-chave para o `Group Join` cláusula, conforme mostrado no exemplo a seguir:  
  
    ```vb#  
    Dim query = From var1 In collection1 _ Join var2 In collection2 _ Group Join var3 In collection3 _ On var2.ID Equals var3 Into Matches = Group _ On var1 Equals var2.ID _ Select JoinID = var1, var2.Name, Matches  
    ```  
  
## Consulte também  
 [Como combinar dados com junções](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Cláusula Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)