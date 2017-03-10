---
title: "O tipo &#39;&lt; typename &gt;&#39; n&#227;o tem nenhum tipo par&#226;metros e, portanto, n&#227;o podem ter argumentos de tipo | Microsoft Docs"
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
  - "bc32045"
  - "vbc32045"
helpviewer_keywords: 
  - "BC32045"
ms.assetid: b86e784c-6718-4585-bd39-2f0982068828
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; n&#227;o tem nenhum tipo par&#226;metros e, portanto, n&#227;o podem ter argumentos de tipo
Uma declaração ou instrução de atribuição inclui um [de](/dotnet/visual-basic/language-reference/statements/of-clause) cláusula ao invocar um tipo não genérico.  
  
 Por sua definição, um *tipo genérico* é uma classe, estrutura, interface, um procedimento ou delegado que funciona em tipos de dados, você pode especificar por meio de um ou mais *parâmetros de tipo*. Quando o uso de código cria um tipo desse tipo genérico, ele fornece um *o argumento de tipo* para cada parâmetro de tipo. Como parte da criação do tipo, cada argumento de tipo substitui todas as ocorrências de seu parâmetro de tipo correspondente no código gerado.  
  
 Parâmetros de tipo são definidos com um `Of` cláusula dentro de parênteses e argumentos de tipo são fornecidos usando um `Of` cláusula dentro dos parênteses. O `Of` cláusula é usada somente quando lidam com tipos genéricos.  
  
 Tipos não genéricos não aceita parâmetros de tipo e você não pode especificar argumentos de tipo quando você invoca um tipo.  
  
 **ID do erro:** BC32045  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia do tipo que você está usando na declaração ou instrução de atribuição.  
  
2.  Se você estiver chamando um tipo não genérico, remova o `Of` cláusula e seus entre parênteses, se houver. Não remova parênteses ao redor de uma lista de argumentos padrão para um procedimento, o delegado ou o construtor de classe.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Como usar uma classe genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)