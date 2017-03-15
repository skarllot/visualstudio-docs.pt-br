---
title: "A restri&#231;&#227;o indireta &#39;&lt; constraint1 &gt;&#39; obtida da restri&#231;&#227;o de par&#226;metro do tipo &#39;&lt; typeparameter1 &gt;&#39; est&#225; em conflito com a restri&#231;&#227;o &#39;&lt; restri&#231;&#227;o2 &gt;&#39; | Microsoft Docs"
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
  - "bc32111"
  - "vbc32111"
helpviewer_keywords: 
  - "BC32111"
ms.assetid: b03b5840-5318-4844-b2da-1bca4c28d097
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A restri&#231;&#227;o indireta &#39;&lt; constraint1 &gt;&#39; obtida da restri&#231;&#227;o de par&#226;metro do tipo &#39;&lt; typeparameter1 &gt;&#39; est&#225; em conflito com a restri&#231;&#227;o &#39;&lt; restri&#231;&#227;o2 &gt;&#39;
Um tipo genérico é declarado com restrições conflitantes devido a uma combinação de restrições diretas e indiretas.  
  
 A instrução a seguir pode gerar esse erro.  
  
 `Public Class testClass(Of t1 As {t2, Class}, t2 As Structure)`  
  
 A restrição indireta `Structure` e a restrição direta `Class` causam um conflito para o parâmetro de tipo `t1`, pois o `Structure` restrição requer que o argumento de tipo correspondente seja tipo de valor, enquanto `Class` requer que ele seja um tipo de referência.  
  
 **ID do erro:** BC32111  
  
### Para corrigir este erro  
  
-   Altere as restrições de parâmetro de tipo para evitar conflitos.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)