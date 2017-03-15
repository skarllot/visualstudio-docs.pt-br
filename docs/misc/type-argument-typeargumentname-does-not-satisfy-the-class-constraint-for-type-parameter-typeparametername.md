---
title: "O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; n&#227;o satisfaz a restri&#231;&#227;o &#39;Class&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O argumento de tipo &#39;&lt; typeargumentname &gt;&#39; n&#227;o satisfaz a restri&#231;&#227;o &#39;Class&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39;
Um argumento de tipo fornecido para um tipo genérico não satisfaz a restrição de tipo de referência no seu parâmetro de tipo correspondente.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade geral, especificando um destes procedimentos:  
  
-   O argumento de tipo deve ser um tipo de valor \(incluem o [estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) restrição\)  
  
-   O argumento de tipo deve ser um tipo de referência \(incluem o [Class \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) restrição\)  
  
 Não é possível especificar `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar uma mais de uma vez.  
  
 **ID do erro:** BC32106  
  
### Para corrigir este erro  
  
-   Selecione um argumento de tipo de qualquer tipo de referência.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Como usar uma classe genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)