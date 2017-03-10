---
title: "&#39;Em&#39; esperado | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36615"
  - "vbc36615"
helpviewer_keywords: 
  - "BC36615"
ms.assetid: 24062dd9-a973-43b6-88d3-c11adc5a3736
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Em&#39; esperado
Um `Aggregate`, `Group By`, ou `Group Join` cláusula foi especificada sem um `Into` operador. Você usa o `Into` operador para identificar as funções agregadas para aplicar ao resultado da consulta e para identificar o membro do tipo do resultado da consulta para conter os resultados agrupados \(usando o `Group` função agregada\).  
  
 **ID do erro:** BC36615  
  
### Para corrigir este erro  
  
1.  Adicionar o `Into` operador para o `Aggregate`, `Group By`, ou `Group Join` cláusula. Este é um exemplo:  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## Consulte também  
 [Cláusula Aggregate](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Cláusula Group By](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Cláusula Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)