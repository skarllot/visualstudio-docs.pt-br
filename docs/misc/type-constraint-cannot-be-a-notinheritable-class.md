---
title: "Restri&#231;&#227;o de tipo n&#227;o pode ser uma classe &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc32060"
  - "bc32060"
helpviewer_keywords: 
  - "BC32060"
ms.assetid: f45cc0b6-7df1-462a-b3df-c526c143e16a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Restri&#231;&#227;o de tipo n&#227;o pode ser uma classe &#39;NotInheritable&#39;
Uma lista de restrições inclui uma classe marcada como [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable).  
  
 Uma lista de restrição em um parâmetro de tipo pode aceitar no máximo uma classe. Um argumento de tipo fornecido para esse parâmetro de tipo deve herdar da classe. Portanto, o parâmetro de tipo não pode aceitar um *lacrado*, ou `NotInheritable`, classe como uma restrição.  
  
 **ID do erro:** BC32060  
  
### Para corrigir este erro  
  
-   Se o parâmetro de tipo deve ser capaz de herdar da classe, e você tem controle sobre a definição da classe, remova o `NotInheritable` declaração da classe.  
  
-   Se a classe deve permanecer `NotInheritable`, você não pode usá\-lo como uma restrição. Remova o nome da classe da lista de restrições.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)