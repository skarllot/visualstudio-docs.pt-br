---
title: "N&#227;o acess&#237;vel &#39;&lt; genericprocedurename &gt;&#39; aceita este n&#250;mero de argumentos de tipo | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o acess&#237;vel &#39;&lt; genericprocedurename &gt;&#39; aceita este n&#250;mero de argumentos de tipo
Uma instrução chama um procedimento genérico que tem mais de uma versão sobrecarregada, mas nenhuma das versões sobrecarregadas define o mesmo número de parâmetros de tipo como o número de argumentos de tipo fornecidos na chamada.  
  
 Se houver apenas uma versão genérica, chamá\-la sem argumentos de tipo e o compilador pode tentar *inferência de tipo*. Para obter mais informações, consulte "Inferência de tipo" em [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). No entanto, se houver mais de uma versão genérica, o compilador não é capaz de escolher entre eles, a menos que você fornecer argumentos de tipo. Se você fornecer um argumento de tipo, você deve fornecer um argumento de tipo para cada parâmetro de tipo que uma das versões sobrecarregadas define.  
  
 **ID do erro:** BC32118  
  
### Para corrigir este erro  
  
-   Decida qual versão que você deseja chamar e, em seguida, forneça o número apropriado de argumentos de tipo sobrecarregada.  
  
## Consulte também  
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)