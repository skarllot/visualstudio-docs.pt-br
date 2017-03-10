---
title: "Restri&#231;&#227;o &#39;Structure&#39; n&#227;o pode ser especificada v&#225;rias vezes para o mesmo par&#226;metro de tipo | Microsoft Docs"
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
  - "bc32102"
  - "vbc32102"
helpviewer_keywords: 
  - "BC32102"
ms.assetid: f4ebd416-7fb9-4a24-a8df-e9ee7ccc2c76
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Restri&#231;&#227;o &#39;Structure&#39; n&#227;o pode ser especificada v&#225;rias vezes para o mesmo par&#226;metro de tipo
Uma lista de restrição inclui o [estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) restrição mais de uma vez.  
  
 Uma lista de restrição em um parâmetro de tipo pode especificar que o argumento de tipo passado para esse parâmetro de tipo deve ser um tipo de valor \(com a `Structure` restrição\) ou deve ser um tipo de referência \(com a [Class \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) restrição\). Não é possível especificar ambos para o mesmo parâmetro de tipo, e você não pode especificar qualquer deles mais de uma vez.  
  
 ID do erro: BC32102  
  
### Para corrigir este erro  
  
-   Remove qualquer redundante `Structure` palavras\-chave. Você deve ter apenas um na lista de restrição.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)