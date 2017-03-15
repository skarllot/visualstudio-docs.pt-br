---
title: "O operador &#39;&lt; operador &gt;&#39; deve ter um ou dois par&#226;metros | Microsoft Docs"
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
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O operador &#39;&lt; operador &gt;&#39; deve ter um ou dois par&#226;metros
Um operador que pode ser um unário ou binário é definido sem parâmetros ou com mais de dois parâmetros.  
  
 Um operador unário\/binário deve ter um ou dois parâmetros.  
  
 **ID do erro:** BC33016  
  
### Para corrigir este erro  
  
-   Ajuste a definição para especificar um ou dois parâmetros.  
  
-   Se você precisar sem parâmetros ou com mais de dois, você deve usar o [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement) para definir uma `Function` procedimento em vez de um operador.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)