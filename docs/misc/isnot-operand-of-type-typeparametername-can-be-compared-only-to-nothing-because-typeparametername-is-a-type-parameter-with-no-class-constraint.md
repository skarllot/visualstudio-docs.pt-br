---
title: "O operando &#39;IsNot&#39; do tipo &#39;&lt; typeparametername &gt;&#39; pode ser comparado apenas a &#39;Nothing&#39; porque &#39;&lt; typeparametername &gt;&#39; &#233; um par&#226;metro de tipo sem nenhuma restri&#231;&#227;o de classe | Microsoft Docs"
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
  - "vbc32097"
  - "bc32097"
helpviewer_keywords: 
  - "BC32097"
ms.assetid: 50283a4b-70e3-4e59-9b9b-65e7cacf5ce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O operando &#39;IsNot&#39; do tipo &#39;&lt; typeparametername &gt;&#39; pode ser comparado apenas a &#39;Nothing&#39; porque &#39;&lt; typeparametername &gt;&#39; &#233; um par&#226;metro de tipo sem nenhuma restri&#231;&#227;o de classe
Um parâmetro de tipo é usado como um operando para o [Operador IsNot](/dotnet/visual-basic/language-reference/operators/isnot-operator) quando o parâmetro de tipo é definido sem que os recursos de [Class \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) palavra\-chave ou nome de classe específico em sua lista de restrições.  
  
 `IsNot` compara dois tipos de referência para determinar se eles apontam para a mesma instância de objeto na memória. Ele não pode tomar um operando que não é um tipo de referência, a menos que o outro operando for [nada](/dotnet/visual-basic/language-reference/nothing).  
  
 **ID do erro:** BC32097  
  
### Para corrigir este erro  
  
-   Se você pode exigir que o argumento de tipo fornecido para esse tipo de parâmetro sempre seja um tipo de referência, adicionar o `Class` palavra\-chave ou nome de classe específico para a lista de restrições para o parâmetro de tipo.  
  
-   Se você não pode solicitar que o argumento de tipo fornecido para esse tipo de parâmetro sempre seja um tipo de referência, remova\-a do `IsNot` expressão. Você não compará\-lo a outros tipos de referência com o `IsNot` operador.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Operadores de comparação no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)