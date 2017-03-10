---
title: "A restri&#231;&#227;o &#39;&lt; constraint1 &gt;&#39; est&#225; em conflito com a restri&#231;&#227;o &#39;&lt; restri&#231;&#227;o2 &gt;&#39; j&#225; especificado para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; | Microsoft Docs"
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
  - "vbc32119"
  - "bc32119"
helpviewer_keywords: 
  - "BC32119"
ms.assetid: 30e6778d-5c2b-4f2d-a136-4e66fa9fbe4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A restri&#231;&#227;o &#39;&lt; constraint1 &gt;&#39; est&#225; em conflito com a restri&#231;&#227;o &#39;&lt; restri&#231;&#227;o2 &gt;&#39; j&#225; especificado para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39;
Um tipo genérico é declarado com restrições conflitantes em um parâmetro de tipo.  
  
 A instrução a seguir pode gerar esse erro.  
  
 `Public Class testClass(Of t As {Structure, Class })`  
  
 As restrições `Structure` e `Class` causam um conflito para o parâmetro de tipo `t`, pois o `Structure` restrição requer que o argumento de tipo correspondente seja tipo de valor, enquanto `Class` requer que ele seja um tipo de referência.  
  
 **ID do erro:** BC32119  
  
### Para corrigir este erro  
  
-   Altere as restrições de parâmetro de tipo para evitar conflitos.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)