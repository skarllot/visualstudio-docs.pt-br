---
title: "&#39;New&#39; n&#227;o pode ser usado em um par&#226;metro de tipo que n&#227;o tem uma restri&#231;&#227;o &#39;New&#39; | Microsoft Docs"
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
  - "bc32046"
  - "vbc32046"
helpviewer_keywords: 
  - "BC32046"
ms.assetid: 7ec6b52d-6fd5-47a0-b4a2-163bfd3dae35
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; n&#227;o pode ser usado em um par&#226;metro de tipo que n&#227;o tem uma restri&#231;&#227;o &#39;New&#39;
Uma instrução de declaração utiliza uma [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator) cláusula especificando um parâmetro de tipo como o tipo a ser criado e o parâmetro de tipo é declarado sem uma `New` restrição.  
  
 Um *restrição* em um tipo de parâmetro impõe uma necessidade em qualquer argumento de tipo passado para esse parâmetro do tipo quando o tipo genérico é criado. O `New` restrição Especifica que o argumento de tipo deve expor um construtor sem parâmetros que o código de criação pode acessar. Isso é o que permite uma `New` cláusula em uma instrução de declaração para criar uma instância desse tipo.  
  
 **ID do erro:** BC32046  
  
### Para corrigir este erro  
  
-   Se você pode exigir o argumento de tipo para expor um construtor sem parâmetros acessível, adicione a `New` restrição à declaração de parâmetro de tipo.  
  
-   Se você não pode solicitar o argumento de tipo para expor um construtor sem parâmetros acessível, remova o `New` cláusula da instrução de declaração. Você não pode garantir que qualquer argumento de tipo passado para esse parâmetro do tipo permite a criação de uma instância.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)