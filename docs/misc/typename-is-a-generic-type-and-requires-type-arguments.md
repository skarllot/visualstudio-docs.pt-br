---
title: "&#39;&lt; typename &gt;&#39; &#233; um tipo gen&#233;rico e requer argumentos de tipo | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; &#233; um tipo gen&#233;rico e requer argumentos de tipo
Uma variável, parâmetro de procedimento ou função de retorno é declarada com o tipo de uma classe genérica ou estrutura, mas a declaração não fornece quaisquer argumentos de tipo.  
  
 Por sua natureza, cada classe genérica e a estrutura é definida com pelo menos um parâmetro de tipo. Quando você usa um tipo genérico para declarar uma classe ou estrutura construída, você deve fornecer um argumento de tipo para cada parâmetro de tipo definido pelo tipo genérico.  
  
 **ID do erro:** BC32076  
  
### Para corrigir este erro  
  
-   Adicione uma lista de tipos à declaração, entre parênteses e começando com o `Of` palavra\-chave.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)