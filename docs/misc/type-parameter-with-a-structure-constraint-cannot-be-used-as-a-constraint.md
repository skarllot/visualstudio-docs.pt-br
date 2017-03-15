---
title: "Par&#226;metro de tipo com uma restri&#231;&#227;o n&#227;o pode ser usada como uma restri&#231;&#227;o &#39;Structure&#39; | Microsoft Docs"
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
  - "vbc32114"
  - "bc32114"
helpviewer_keywords: 
  - "BC32114"
ms.assetid: 442b2048-9dc4-4223-bcfc-4d96bf8d14de
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metro de tipo com uma restri&#231;&#227;o n&#227;o pode ser usada como uma restri&#231;&#227;o &#39;Structure&#39;
Um parâmetro de tipo com uma `Structure` restrição é usada como a restrição para outro parâmetro do tipo.  
  
 O `Structure` restrição requer que o argumento passado para o parâmetro do tipo seja um tipo de valor. No entanto, um tipo de valor não pode ser implementado ou herdado, portanto não faz sentido usá\-lo como uma restrição, que exigiria o outro parâmetro do tipo para implementá\-lo ou herdar a partir dele.  
  
 A interpretação somente significativa nesta situação é que ambos os argumentos de tipo devem ser do mesmo tipo exato. Se esse for o caso, o tipo genérico precisa apenas de um parâmetro de tipo.  
  
 A instrução a seguir pode gerar esse erro.  
  
 `Class c1(Of t1 As Structure, t2 As t1)`  
  
 O tipo passado para `t2` não pode implementar ou herdar o tipo passado para `t1`, porque o tipo passado para `t1` deve ser um tipo de valor.  
  
 **ID do erro:** BC32114  
  
### Para corrigir este erro  
  
-   Remova o parâmetro do tipo restringido a `Structure` da lista de restrições no parâmetro de tipo.  
  
-   Se ambos os parâmetros de tipo exigirem o mesmo tipo de valor, defina o tipo genérico com apenas um parâmetro de tipo.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)