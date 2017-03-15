---
title: "&#39;IsNot&#39; requer operandos que tenham tipos de refer&#234;ncia, mas este operando tem o tipo de valor &#39;&lt; typename &gt;&#39;. | Microsoft Docs"
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
  - "bc31419"
  - "vbc31419"
helpviewer_keywords: 
  - "BC31419"
ms.assetid: c44d2936-8c07-443a-b320-ac2bfbc1e9ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;IsNot&#39; requer operandos que tenham tipos de refer&#234;ncia, mas este operando tem o tipo de valor &#39;&lt; typename &gt;&#39;.
Uma expressão usa a [Operador IsNot](/dotnet/visual-basic/language-reference/operators/isnot-operator) com o operando do tipo de pelo menos um valor.  
  
 O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes. Ele compara os valores de ponteiro de tipos de referência e não faz sentido com tipos de valor.  
  
 **ID do erro:** BC31419  
  
### Para corrigir este erro  
  
-   Se você pretende comparar os valores dos dois tipos de valor, use o `=` ou `<>` operador de comparação.  
  
-   Se você pretende comparar os ponteiros de dois tipos de referência, certifique\-se de que você está usando referências de objeto para ambos os operandos. Você pode usar variáveis de referência ou elementos, como o [Me](http://msdn.microsoft.com/pt-br/a65973c7-cf06-4547-9b25-9fba885525c2) palavra\-chave, que se comportam como fazer referência a variáveis.  
  
## Consulte também  
 [Operadores de comparação no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Como testar se dois objetos são iguais](../Topic/How%20to:%20Test%20Whether%20Two%20Objects%20Are%20the%20Same%20\(Visual%20Basic\).md)