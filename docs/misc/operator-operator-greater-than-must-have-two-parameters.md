---
title: "Operador &#39;&lt; operador &gt;&#39; deve ter dois par&#226;metros | Microsoft Docs"
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
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &#39;&lt; operador &gt;&#39; deve ter dois par&#226;metros
Um operador binário é definido com menos de dois ou mais de dois parâmetros.  
  
 Um operador binário deve ter exatamente dois parâmetros.  
  
 **ID do erro:** BC33015  
  
### Para corrigir este erro  
  
-   Ajuste a definição para especificar exatamente dois parâmetros.  
  
-   Se você precisar apenas de um parâmetro, você deve definir um operador unário.  
  
-   Se você precisar sem parâmetros ou com mais de dois, você deve usar o [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement) para definir uma `Function` procedimento em vez de um operador.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)