---
title: "&#39;,&#39; Esperado | Microsoft Docs"
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
  - "vbc36605"
  - "bc36605"
helpviewer_keywords: 
  - "BC36605"
ms.assetid: d0397b6e-bfc2-400c-92fc-efe82036cfdb
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;,&#39; Esperado
Um `Order By` ou `Group By` cláusula foi especificada sem o `By` palavra\-chave.  
  
 **ID do erro:** BC36605  
  
### Para corrigir este erro  
  
1.  Adicionar o `By` palavra\-chave para a `Order By` ou `Group By` cláusula. Este é um exemplo:  
  
    ```vb#  
    Dim customersByCountry = From cust In customers _  
                             Order By cust.Country, cust.City _  
                             Group By CountryName = cust.Country _  
                             Into RegionalCustomers = Group, Count() _  
                             Order By CountryName  
    ```  
  
## Consulte também  
 [Como classificar resultados de consulta](../Topic/How%20to:%20Sort%20Query%20Results%20by%20Using%20LINQ%20\(Visual%20Basic\).md)   
 [Cláusula Order By](/dotnet/visual-basic/language-reference/queries/order-by-clause)   
 [Cláusula Group By](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)