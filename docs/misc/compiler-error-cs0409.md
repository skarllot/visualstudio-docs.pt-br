---
title: "CS0409 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0409 de erro do compilador
Uma cláusula de restrição já foi especificada para o parâmetro de tipo ' tipo '. Todas as restrições para um parâmetro de tipo devem ser especificadas em um único onde cláusula.  
  
 Várias cláusulas de restrição \(onde cláusulas\) foi encontrado para um parâmetro de tipo único. Remover where estranhas cláusula, ou corrija where cláusulas para que um parâmetro de tipo exclusivo em cada cláusula.  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```