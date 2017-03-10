---
title: "O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; deve ter um construtor de inst&#226;ncia sem par&#226;metros p&#250;blicos para satisfazer &#224; restri&#231;&#227;o &#39;New&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32083"
  - "BC32083"
helpviewer_keywords: 
  - "BC32083"
ms.assetid: 56bf25f1-375c-4b5d-9969-45eba8b3b66c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; deve ter um construtor de inst&#226;ncia sem par&#226;metros p&#250;blicos para satisfazer &#224; restri&#231;&#227;o &#39;New&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39;
Um argumento de tipo fornece um tipo sem um construtor sem parâmetros acessível para um parâmetro de tipo com o [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator) restrição.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Um requisito possível é que o argumento de tipo deve expor um construtor sem parâmetros que o código de criação pode acessar. Para especificar esse requisito, a lista de restrições inclui o `New` restrição.  
  
 **ID do erro:** BC32083  
  
### Para corrigir este erro  
  
1.  Verifique se o nome do tipo genérico e o nome do tipo no argumento de tipo estão escritos corretamente.  
  
2.  Escolha um tipo para o argumento de tipo que expõe um construtor acessível sem parâmetros. Não é possível chamar este tipo genérico particular, a menos que você pode fornecer um argumento de tipo para este parâmetro de tipo.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Como usar uma classe genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)