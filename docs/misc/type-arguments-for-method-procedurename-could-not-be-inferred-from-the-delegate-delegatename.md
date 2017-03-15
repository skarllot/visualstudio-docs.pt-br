---
title: "Argumentos de tipo para o m&#233;todo &#39;&lt; procedurename &gt;&#39; n&#227;o foi poss&#237;vel inferir a partir do delegado &#39;&lt; nomedelegado &gt;&#39; | Microsoft Docs"
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
  - "vbc30952"
  - "bc30952"
helpviewer_keywords: 
  - "BC30952"
ms.assetid: 5eb804ce-2e93-4668-b655-7fe00815e552
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos de tipo para o m&#233;todo &#39;&lt; procedurename &gt;&#39; n&#227;o foi poss&#237;vel inferir a partir do delegado &#39;&lt; nomedelegado &gt;&#39;
Uma instrução de atribuição usa `AddressOf` para atribuir o endereço de um genérico procedimento para um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.  
  
 Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico. Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo. Se o contexto não fornece informação suficiente para o compilador inferir os tipos, ele gera um erro.  
  
 **ID do erro:** BC30952  
  
### Para corrigir este erro  
  
-   Especificar os argumentos de tipo para o procedimento genérico de `AddressOf` expressão.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)