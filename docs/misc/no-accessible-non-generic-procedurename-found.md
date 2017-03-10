---
title: "N&#227;o acess&#237;vel n&#227;o gen&#233;rico &#39;&lt; procedurename &gt;&#39; encontrado | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o acess&#237;vel n&#227;o gen&#233;rico &#39;&lt; procedurename &gt;&#39; encontrado
Uma instrução chama um procedimento que tem mais de uma versão sobrecarregada, mas todas as versões sobrecarregadas são genéricas e a chamada não fornece argumentos de tipo.  
  
 Se houver apenas uma versão genérica e chamá\-la sem argumentos de tipo, o compilador pode tentar *inferência de tipo*. Para obter mais informações, consulte "Inferência de tipo" em [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). No entanto, se houver mais de uma versão genérica, o compilador não é capaz de escolher entre eles, a menos que você fornecer argumentos de tipo. Se você fornecer um argumento de tipo, você deve fornecer um argumento de tipo para cada parâmetro de tipo que uma das versões sobrecarregadas define.  
  
 **ID do erro:** BC32117  
  
### Para corrigir este erro  
  
-   Chame o procedimento com uma lista de argumentos de tipo.  
  
## Consulte também  
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)