---
title: "Somente os operadores de convers&#227;o podem ser declarados &#39;&lt; palavra-chave &gt;&#39; | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Somente os operadores de convers&#227;o podem ser declarados &#39;&lt; palavra-chave &gt;&#39;
Um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) especifica [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ou [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) quando o operador não é um operador de conversão.  
  
 Cada operador deve ser declarado como [Público](/dotnet/visual-basic/language-reference/modifiers/public) e [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared). No entanto, somente um operador de conversão pode ser declarado com [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ou [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), mas não ambos.  
  
 Uma definição do operador, opcionalmente, pode incluir o [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads) e [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows) palavras\-chave. Não há outras palavras\-chave é permitidos em um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 **ID do erro:** BC33019  
  
### Para corrigir este erro  
  
1.  Remover o `Widening` ou `Narrowing` palavra\-chave da definição do operador. Eles não se aplicam, porque nenhuma conversão de tipos está ocorrendo.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)