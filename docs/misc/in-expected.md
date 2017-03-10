---
title: "&#39;In&#39; esperado | Microsoft Docs"
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
  - "bc36607"
  - "vbc36607"
helpviewer_keywords: 
  - "BC36607"
ms.assetid: f390bca5-12fe-4fe1-bd86-7f8ab66dfbd8
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;In&#39; esperado
Um `From` ou `Aggregate` cláusula foi especificada sem um `In` operador. Você usa o `In` operador para identificar a coleção para consulta.  
  
 **ID do erro:** BC36607  
  
### Para corrigir este erro  
  
1.  Adicionar o `In` campos de operador e a chave para o `From` ou `Aggregate` cláusula. Este é um exemplo:  
  
    ```vb#  
    Dim names = From pers In people Select pers.FirstName, pers.LastName  
    ```  
  
## Consulte também  
 [Cláusula From](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Cláusula Aggregate](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)