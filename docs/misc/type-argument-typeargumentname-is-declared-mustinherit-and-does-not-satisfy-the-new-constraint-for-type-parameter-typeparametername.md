---
title: "O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; foi declarado &#39;MustInherit&#39; e n&#227;o satisfaz a restri&#231;&#227;o &#39;New&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32082"
  - "BC32082"
helpviewer_keywords: 
  - "BC32082"
ms.assetid: 597e5944-a61b-4858-ada5-efb80b27f26b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; foi declarado &#39;MustInherit&#39; e n&#227;o satisfaz a restri&#231;&#227;o &#39;New&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39;
Um tipo genérico é invocado com um `MustInherit` classe como um argumento de tipo, enquanto o parâmetro do tipo correspondente é declarado com o `New` restrição.  
  
 O `New` restrição requer que o tipo passado no argumento de tipo correspondente deve oferecer suporte a criação de objetos. No entanto, um *abstrato* classe, isto é, uma classe declarada como `MustInherit`, não expõe nenhum construtor porque você não pode criar nenhum objeto dele.  
  
 **ID do erro:** BC32082  
  
### Para corrigir este erro  
  
1.  Se a classe usada no argumento de tipo não precisa ser abstrata, remova o `MustInherit` palavra\-chave da sua declaração.  
  
2.  Se a classe usada no argumento de tipo precisa ser abstrata mas não precisa ser usado para construir o tipo genérico, em seguida, passe uma classe diferente no argumento de tipo.  
  
3.  Se o parâmetro de tipo correspondente não precisa criar os objetos do tipo passado para ele e, em seguida, remover o `New` restrição de sua declaração.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)