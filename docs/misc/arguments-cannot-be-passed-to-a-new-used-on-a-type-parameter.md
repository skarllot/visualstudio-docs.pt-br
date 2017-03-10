---
title: "Argumentos n&#227;o podem ser passados para um &#39;New&#39; usado em um par&#226;metro de tipo | Microsoft Docs"
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
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos n&#227;o podem ser passados para um &#39;New&#39; usado em um par&#226;metro de tipo
Uma declaração ou instrução de atribuição chama um tipo genérico e fornece argumentos de construtor para um parâmetro de tipo que tem o [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator) restrição.  
  
 Uma lista de restrição em um parâmetro de tipo pode especificar que o argumento passado para esse parâmetro do tipo deve expor um construtor sem parâmetros que o código de criação pode acessar. Um parâmetro de tipo não pode exigir um construtor que usa parâmetros e um parâmetro de tipo com o `New` restrição não pode aceitar um construtor.  
  
 **ID do erro:** BC32085  
  
### Para corrigir este erro  
  
-   Remova a lista de argumentos após o argumento de tipo na instrução chamando o tipo genérico. Você não pode passar argumentos de construtor para o parâmetro de tipo correspondente.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)