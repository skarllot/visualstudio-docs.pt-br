---
title: "A restri&#231;&#227;o &#39;New&#39; e &#39; Structure &#39; n&#227;o podem ser combinados | Microsoft Docs"
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
  - "bc32103"
  - "vbc32103"
helpviewer_keywords: 
  - "BC32103"
ms.assetid: 5418b420-a014-4006-84aa-20ddac6739e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A restri&#231;&#227;o &#39;New&#39; e &#39; Structure &#39; n&#227;o podem ser combinados
Uma lista de restrição inclui tanto o [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator) restrição e o [estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) restrição.  
  
 Uma lista de restrição em um parâmetro de tipo pode especificar que o argumento de tipo passado para esse parâmetro de tipo deve ser um tipo de valor \(com a `Structure` restrição\) ou deve ser um tipo de referência \(com a [Class \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) restrição\). Não é possível especificar ambos para o mesmo parâmetro de tipo, e você não pode especificar qualquer deles mais de uma vez.  
  
 O `New` restrição Especifica que o argumento de tipo deve expor um construtor sem parâmetros que o código de criação pode acessar. No entanto, uma estrutura não pode ter um construtor sem parâmetros compartilhado. Portanto, o `New` e `Structure` restrições estão em conflito.  
  
 **ID do erro:** BC32103  
  
### Para corrigir este erro  
  
1.  Decida se deseja exigir um tipo de valor ou um tipo de referência para o argumento de tipo.  
  
2.  Se desejar que o argumento de tipo para ser um tipo de valor, remova o `New` palavra\-chave da lista de restrições.  
  
3.  Se desejar que o argumento de tipo para ser um tipo de referência, remova o `Structure` palavra\-chave da lista de restrições.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)