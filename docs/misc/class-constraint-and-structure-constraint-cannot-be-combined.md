---
title: "Restri&#231;&#227;o &#39;Class&#39; e &#39; Structure &#39; n&#227;o podem ser combinados | Microsoft Docs"
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
  - "vbc32104"
  - "bc32104"
helpviewer_keywords: 
  - "BC32104"
ms.assetid: f41a581b-afca-4173-bc82-b35ed49caba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Restri&#231;&#227;o &#39;Class&#39; e &#39; Structure &#39; n&#227;o podem ser combinados
Uma lista de restrição inclui tanto o [Class \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) restrição e o [estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) restrição.  
  
 Uma lista de restrição em um parâmetro de tipo pode especificar que o argumento de tipo passado para esse parâmetro de tipo deve ser um tipo de valor \(com a `Structure` restrição\) ou deve ser um tipo de referência \(com a `Class` restrição\). Não é possível especificar ambos para o mesmo parâmetro de tipo, e você não pode especificar qualquer deles mais de uma vez.  
  
 **ID do erro:** BC32104  
  
### Para corrigir este erro  
  
1.  Decida se deseja exigir um tipo de valor ou um tipo de referência para o argumento de tipo.  
  
    -   Se desejar que o argumento de tipo para ser um tipo de valor, remova o `Class` palavra\-chave da lista de restrições.  
  
    -   Se desejar que o argumento de tipo para ser um tipo de referência, remova o `Structure` palavra\-chave da lista de restrições.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)